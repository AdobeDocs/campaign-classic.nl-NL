---
product: campaign
title: Campagne SDK integreren
description: Leer hoe u campagne SDK kunt integreren in uw mobiele app
feature: Mobile SDK Integration, Push
role: User, Developer
hide: true
hidefromtoc: true
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: ad6f3f2cf242d28de9e6da5cec100e096c5cbec2
workflow-type: tm+mt
source-wordcount: '983'
ht-degree: 3%

---

# Campagne SDK integreren met uw app {#integrating-campaign-sdk-into-the-mobile-application}

>[!CAUTION]
>
>Adobe raadt u ten zeerste aan de Adobe Experience Platform Mobile SDK te gebruiken door de Adobe Campaign-extensie te configureren in de gebruikersinterface voor gegevensverzameling. De Adobe Experience Platform Mobile-SDK maakt de Experience Cloud-oplossingen en -services van Adobe in uw mobiele apps mogelijk. De configuratie van SDK&#39;s wordt beheerd via de gebruikersinterface voor dataverzameling voor een flexibele configuratie en uitbreidbare integraties op basis van regels. [&#x200B; leer meer in de documentatie van Adobe Developer &#x200B;](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.

Om Campagne SDK (eerder genoemd geworden Neolane SDK) te krijgen, contacteer [&#x200B; de Zorg van de Klant van Adobe &#x200B;](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

Om meer op de verschillende gesteunde versies van Android en van iOS te leren, verwijs naar de [&#x200B; matrijs van de Verenigbaarheid &#x200B;](../../rn/using/compatibility-matrix.md#MobileSDK).

U vindt de integratiestappen voor Campagne SDK hieronder.

+++**het Lagen Campagne SDK**

* **in Android**: **neolane_sdk-release.aar** dossier moet aan het project worden verbonden.

  Met de volgende machtiging krijgt u toegang tot de Adobe Campaign-server:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
  ```

  Met de volgende machtiging kunt u de unieke id van een mobiel herstellen:

  ```
  <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
  ```

  Vanaf versie 1.0.24 van de SDK wordt deze machtiging alleen gebruikt voor versies ouder dan Android 6.0.

  Vanaf versie 1.0.26 van de SDK wordt deze machtiging niet meer gebruikt.

* **in iOS**: **libNeolaneSDK.a** en **Neolane_SDK.h** dossiers moeten met het project worden verbonden. Van versie 1.0.24 van SDK, wordt de optie **ENABLE_BITCODE** geactiveerd.

  >[!NOTE]
  >
  >Voor versie 1.0.25 van SDK, zijn de vier architecturen beschikbaar in het {**dossier 0} Neolane_SDK.h.**

+++

+++**Verklarend integratiemontages**

Om Campagne SDK in de mobiele toepassing te integreren, moet de functionele beheerder de ontwikkelaar de volgende informatie verstrekken:

* **een integratiesleutel**: om het platform van Adobe Campaign toe te laten om de mobiele toepassing te identificeren.

  >[!NOTE]
  >
  >Deze integratietoets wordt ingevoerd in de Adobe Campaign-console, op het tabblad **[!UICONTROL Information]** van de service die is toegewezen aan de mobiele toepassing. Verwijs naar de [&#x200B; documentatie van de Campagne v8 &#x200B;](https://experienceleague.adobe.com/docs/campaign/campaign-v8/send/push/push-settings.html){target="_blank"}.

* **het volgen URL van A**: die het adres van de het volgen van Adobe Campaign server aanpast.
* **A marketing URL**: om de inzameling van abonnementen toe te laten.

* **in Android**:

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
  ```

* **in iOS**:

  ```
  Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl setMarketingHost:strMktHost];
  [nl setTrackingHost:strTckHost];
  [nl setIntegrationKey:strIntegrationKey];
  ```

+++

+++**functie van de Registratie**

Met de registratiefunctie kunt u:

* Stuur de bericht-id of push-id (deviceToken voor iOS en registrationID voor Android) naar Adobe Campaign.
* de afstemmingssleutel of de gebruikersnaam herstellen (bijvoorbeeld e-mail- of accountnummer)

* **in Android**:

  ```
  void registerInNeolane(String registrationId, String userKey, Context context)
  {
   try{
    Neolane.getInstance().registerDevice(registrationToken, userKey, null, context);
   } catch (NeolaneException e){
    //...
   } catch (IOException e){
    //...
   }
  }
  ```

  Als u FCM (het Overseinen van de Wolk van de Vuurstand) gebruikt, adviseren wij u de **registerDevice** functie wanneer het roepen van de **onTokenRefresh** functie om Adobe Campaign van de verandering in het mobiele apparatenteken van de gebruiker op de hoogte te brengen.

  ```
  public class NeoTripFirebaseInstanceIDService extends FirebaseInstanceIdService {
    @Override
    public void onTokenRefresh() {
      String registrationToken = FirebaseInstanceId.getInstance().getToken();
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      ...
      ...
      // Neolane Registration
      neolaneAs.registerDevice(registrationToken, userKey, additionnalParam, this, new NeolaneAsyncRunner.RequestListener() {
      public void onComplete(String e, Object state) { ... }
      public void onNeolaneException(NeolaneException e, Object state) { ... }
      public void onIOException(IOException e, Object state) { ... }
      });
      ...
      ...
    }
  }
  ```

* **in iOS**:

  ```
  // Callback called on successful registration to the APNs
  - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
  {
      // Pass the token to Adobe Campaign
      Neolane_SDK *nl = [Neolane_SDK getInstance];
      [nl registerDevice:tokenString:self.userKey:dic];
  }
  ```

+++

+++**het Volgen functie**

* **in Android**:

  Met de trackingfuncties kunt u berichtactities (geopend) en berichtweergaven (screenshot) bijhouden.

  Om de berichtvertoning te volgen (die door **wordt gedaan te roepen notifyReceive** functie van SDK), volg hieronder de implementatie. Merk op dat als u FCM (het Overseinen van de Wolk van de Vuurbasis) gebruikt, adviseren wij u om de **notifyReceive** functie te gebruiken wanneer de **onMessageReceived** functie door het systeem van Android wordt geroepen.

  ```
  package com.android.YourApplication;
  
  import android.content.Context;
  import android.content.SharedPreferences;
  import android.os.Bundle;
  import android.util.Log;
  
  import com.google.firebase.messaging.FirebaseMessagingService;
  import com.google.firebase.messaging.RemoteMessage;
  
  import java.util.Iterator;
  import java.util.Map;
  import java.util.Map.Entry;
  
  public class YourApplicationFirebaseMessagingService extends FirebaseMessagingService {
    private static final String TAG = "MyFirebaseMsgService";
  
    @Override
    public void onMessageReceived(RemoteMessage message) {
      Log.d(TAG, "Receive message from: " + message.getFrom());
      Map<String,String> payloadData = message.getData();
      final Bundle extras = new Bundle();
      final Iterator<Entry<String, String>> iter = payloadData.entrySet().iterator();
      while(iter.hasNext())
      {
        final Entry<String, String>  entry =iter.next();
        extras.putString(entry.getKey(), entry.getValue());
      }
  
      SharedPreferences settings = this.getSharedPreferences(YourApplicationActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      String mesg = payloadData.get("_msg");
      String title = payloadData.get("title");
      String url = payloadData.get("url");
      String messageId = payloadData.get("_mId");
      String deliveryId = payloadData.get("_dId");
      YourApplicationActivity.handleNotification(this, mesg, title, url, messageId, deliveryId, extras);
    }
  }
  ```

  ```
  public static void handleNotification(Context context, String message, String title, String url, String messageId, String deliveryId, Bundle extras){
      if( message == null ) message = "No Content";
      if( title == null )   title = "No title";
      if( url == null )     url = "https://www.tripadvisor.fr";
      int iconId = R.drawable.notif_neotrip;
  
    // notify Neolane that a notification just arrived
    SharedPreferences settings = context.getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
    Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
    Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));
    Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
    NeolaneAsyncRunner nas = new NeolaneAsyncRunner(Neolane.getInstance());
    nas.notifyReceive(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
      public void onNeolaneException(NeolaneException arg0, Object arg1) {}
      public void onIOException(IOException arg0, Object arg1) {}
      public void onComplete(String arg0, Object arg1){}
    });
    if (yourApplication.isActivityVisible())
      {
        Log.i("INFO", "The application has the focus" );
        ...
      }
      else
      {
        // notification creation :
        NotificationManager notificationManager = (NotificationManager) context.getSystemService(Context.NOTIFICATION_SERVICE);
        Notification notification;
  
        // Activity to start :
        Intent notifIntent = new Intent(context.getApplicationContext(), NotificationActivity.class);
        notifIntent.putExtra("notificationText", message);
        notifIntent.putExtra(NotificationActivity.NOTIFICATION_URL_KEYNAME, url);
        notifIntent.putExtra("_dId", deliveryId);
        notifIntent.putExtra("_mId", messageId);
        notifIntent.addFlags(Intent.FLAG_ACTIVITY_NEW_TASK);
        PendingIntent contentIntent = PendingIntent.getActivity(context, 1, notifIntent, PendingIntent.FLAG_UPDATE_CURRENT);
  
        notification = new Notification.Builder(context)
                .setContentTitle(title)
                .setContentText(message)
                .setSmallIcon(iconId)
                .setContentIntent(contentIntent)
                .build();
  
        // launch the notification :
        notification.flags |= Notification.FLAG_AUTO_CANCEL;
        notificationManager.notify(Integer.valueOf(messageId), notification);
      }
  }
  ```

  Hier is een implementatievoorbeeld voor het volgen van een bericht open (die door de **wordt uitgevoerd notifyOpening** functie van SDK te roepen). De **NotificationActivity** klasse beantwoordt aan die wordt gebruikt om tot het **notifIntent** voorwerp in het vorige voorbeeld te leiden.

  ```
  public class NotificationActivity extends Activity {
  public void onCreate(Bundle savedBundle) {
    [...]
    Bundle extra = getIntent().getExtras();
    if (extra != null) {
      // reinit the acc sdk
      SharedPreferences settings = getSharedPreferences(NeoTripActivity.APPLICATION_PREF_NAME, Context.MODE_PRIVATE);
      Neolane.getInstance().setIntegrationKey(settings.getString(NeoTripActivity.APPUUID_NAME, NeoTripActivity.DFT_APPUUID));
      Neolane.getInstance().setMarketingHost(settings.getString(NeoTripActivity.SOAPRT_NAME, NeoTripActivity.DFT_SOAPRT));               
      Neolane.getInstance().setTrackingHost(settings.getString(NeoTripActivity.TRACKRT_NAME, NeoTripActivity.DFT_TRACKRT));
  
      // Get the messageId and the deliveryId to do the tracking
      String deliveryId = extra.getString("_dId");
      String messageId = extra.getString("_mId");
      if (deliveryId != null && messageId != null) {
        try {
          Neolane.getInstance().notifyOpening(Integer.valueOf(messageId), Integer.valueOf(deliveryId));
        } catch (NeolaneException e) {
          // ...
        } catch (IOException e) {
          // ...
        }
      }
    }
   }
  }
  ```

* **in iOS**:

  Met de functie Tekstspatiëring kunt u bijhouden wanneer meldingen zijn geactiveerd (wordt geopend).

  ```
  (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
  {
  if( launchOptions ) { // Retrieve notification parameters here ... // Track application opening Neolane_SDK
  *nl = [Neolane_SDK getInstance]; [nl track:launchOptions:NL_TRACK_CLICK]; } 
  ...  
  completionHandler(UIBackgroundFetchResultNoData);
  }
  ```

  >[!NOTE]
  >
  >Vanaf versie 7.0 roept het besturingssysteem deze functie alleen aan als de functie **`application:didReceiveRemoteNotification:fetchCompletionHandler`** is geïmplementeerd. De functie **`application:didReceiveRemoteNotification`** wordt daarom niet aangeroepen.

+++

+++**Stille bericht het volgen**

Met iOS kunt u meldingen op de achtergrond verzenden, een melding of gegevens die rechtstreeks naar een mobiele toepassing worden verzonden zonder deze weer te geven. Met Adobe Campaign kun je ze volgen.

Volg het onderstaande voorbeeld om je melding op te volgen:

```
// AppDelegate.m
...
...
#import "AppDelegate.h"
#import "Neolane_SDK.h"
...
...
// Callback called when the application is already launched (whether the application is running foreground or background)
- (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions fetchCompletionHandler:(void (^)(UIBackgroundFetchResult))completionHandler
{
 NSLog(@"IN didReceiveRemoteNotification:fetchCompletionHandler");
 if (launchOptions) NSLog(@"IN launchOptions: %@", [launchOptions description]);
 NSLog(@"Application state: %ld", (long)application.applicationState);

 // Silent Notification (specific case, can use NL_TRACK_RECEIVE as the user doesn't have click/open the notification)
 if ([launchOptions[@"aps"][@"content-available"] intValue] == 1 )
       {
  NSLog(@"Silent Push Notification");
  ...  
  ...
  //Call receive tracking
        Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl track:launchOptions:NL_TRACK_RECEIVE];

  completionHandler(UIBackgroundFetchResultNoData); //Do not show notification
  return;
 }  
 ...
 ...
        completionHandler(UIBackgroundFetchResultNoData);
}
```

+++

+++**RegisterDeviceStatus afgevaardigde**

>[!NOTE]
>
>Dit is exclusief voor iOS.

In iOS, staat het gedelegeerde protocol u toe om het resultaat van de **registerDevice** vraag te krijgen en kan worden gebruikt om te weten als een fout tijdens registratie voorkwam.

Het **registerDeviceStatus** prototype is:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**Status** staat u toe om te weten of een registratie slaagde of als een fout voorkwam.

**ErrorReason** voorziet u van meer informatie over de fouten die voorkwamen. Raadpleeg de onderstaande tabel voor meer informatie over beschikbare fouten en beschrijvingen.

<table> 
 <thead>
  <tr>
   <th> Status <br /> </th>
   <th> Beschrijving<br /> </th>
   <th> ErrorReason <br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> Registratie is voltooid <br /> </td>
   <td> EMPTY <br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedMarketingServerHostnameEmpty <br /> </td>
   <td> De ACC marketing server hostname is leeg of niet plaats.<br /> </td>
   <td> EMPTY <br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedIntegrationKeyEmpty <br /> </td>
   <td> De integratietoets is leeg of niet ingesteld.<br /> </td>
   <td> EMPTY <br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedConnectionIssue <br /> </td>
   <td> Verbinding met ACC <br /> </td>
   <td> Meer informatie (in OS huidige taal) <br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedUnknownUID<br /> </td>
   <td> De verstrekte UUID (integratiesleutel) is onbekend.<br /> </td>
   <td> EMPTY <br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedUnexpectedError <br /> </td>
   <td> Onverwachte fout teruggekeerd aan server ACC.<br /> </td>
   <td> Het foutenbericht aan ACC is teruggekeerd.<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** protocol en **registerDeviceStatus** gedelegeerd definitie is als volgt:

```
//  Neolane_SDK.h
//  Neolane SDK
..
.. 
// Register Device Status Enum
typedef NS_ENUM(NSUInteger, ACCRegisterDeviceStatus) {
 ACCRegisterDeviceStatusSuccess,                               // Resistration Succeed
 ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty,   // The ACC marketing server hostname is Empty or not set
 ACCRegisterDeviceStatusFailureIntegrationKeyEmpty,            // The integration key is empty or not set
 ACCRegisterDeviceStatusFailureConnectionIssue,                // Connection issue with ACC, more information in errorReason
 ACCRegisterDeviceStatusFailureUnknownUUID,                    // The provided UUID (integration key) is unknown
 ACCRegisterDeviceStatusFailureUnexpectedError                 // Unexpected error returned by ACC server, more information in errorReason
};
// define the protocol for the registerDeviceStatus delegate
@protocol Neolane_SDKDelegate <NSObject>
@optional
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason;
@end
@interface Neolane_SDK: NSObject {
} 
...
...
// registerDeviceStatus delegate
@property (nonatomic, weak) id <Neolane_SDKDelegate> delegate;
...
...
@end
```

Om **registerDeviceStatus** afgevaardigde uit te voeren, volg deze stappen:

1. Voer **setDelegate** tijdens de initialisering van SDK uit.

   ```
   // AppDelegate.m
   ...
   ... 
   - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
   {
   ...
   ...
    // Get the stored settings
   
    NSUserDefaults *defaults = [NSUserDefaults standardUserDefaults];
    NSString *strMktHost = [defaults objectForKey:@"mktHost"];
    NSString *strTckHost = [defaults objectForKey:@"tckHost"];
    NSString *strIntegrationKey = [defaults objectForKey:@"integrationKey"];
    userKey = [defaults objectForKey:@"userKey"];
   
    // Configure Neolane SDK on first launch
    Neolane_SDK *nl = [Neolane_SDK getInstance];
    [nl setMarketingHost:strMktHost];
    [nl setTrackingHost:strTckHost];
    [nl setIntegrationKey:strIntegrationKey];
    [nl setDelegate:self];    // HERE
   ...
   ...
   }
   ```

1. Voeg het protocol in **toe@interface** van uw klasse.

   ```
   //  AppDelegate.h
   
   #import <UIKit/UIKit.h>
   #import <CoreLocation/CoreLocation.h>
   #import "Neolane_SDK.h"
   
   @class LandingPageViewController;
   
   @interface AppDelegate : UIResponder <UIApplicationDelegate, CLLocationManagerDelegate, Neolane_SDKDelegate> {
       CLLocationManager *locationManager;
       NSString *userKey;
       NSString *mktServerUrl;
       NSString *tckServerUrl;
       NSString *homeURL;
       NSString *strLandingPageUrl;
       NSTimer *timer;
   }
   ```

1. Voer de afgevaardigde in **AppDelegate** uit.

   ```
   //  AppDelegate.m
   
   #import "AppDelegate.h"
   #import "Neolane_SDK.h"
   #import "LandingPageViewController.h"
   #import "RootViewController.h"
   ...
   ...
   - (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status :(NSString *) errorReason
   {
       NSLog(@"registerStatus: %lu",status);
   
       if ( errorReason != nil )
           NSLog(@"errorReason: %@",errorReason);
   
       if( status == ACCRegisterDeviceStatusSuccess )
       {
           // Registration successful
           ...
           ...
       }
       else { // An error occurred
           NSString *message;
           switch ( status ){
               case ACCRegisterDeviceStatusFailureUnknownUUID:
                   message = @"Unkown IntegrationKey (UUID)";
                   break;
               case ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty:
                   message = @"Marketing URL not set or Empty";
                   break;
               case ACCRegisterDeviceStatusFailureIntegrationKeyEmpty:
                   message = @"Integration Key not set or empty";
                   break;
               case ACCRegisterDeviceStatusFailureConnectionIssue:
                   message = [NSString stringWithFormat:@"%@ %@",@"Connection issue:",errorReason];
                   break;
               case ACCRegisterDeviceStatusFailureUnexpectedError:
               default:
                   message = [NSString stringWithFormat:@"%@ %@",@"Unexpected Error",errorReason];
                   break;
           }
    ...
    ...
       }
   }
   @end
   ```

+++

+++**Variabelen**

Met de variabelen kunt u het gedrag van mobiele toepassingen definiëren nadat u een melding hebt ontvangen. Deze variabelen moeten in de mobiele toepassingscode en in de console van Adobe Campaign, in het **[!UICONTROL Variables]** lusje in de specifieke mobiele toepassing (zie [&#x200B; Vormend een mobiele toepassing in Adobe Campaign &#x200B;](configuring-the-mobile-application.md)) worden bepaald. Hier is een voorbeeld van een code waarmee een mobiele toepassing toegevoegde variabelen in een melding kan verzamelen. In ons voorbeeld gebruiken we de variabele &quot;VAR&quot;.

* **in Android**:

  ```
  public void onReceive(Context context, Intent intent) {
       ...
      String event = intent.getStringExtra("VAR");
       ...
  }
  ```

* **in iOS**:

  ```
  - (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
  {
      ....
      if( launchOptions )
      {
          // When application is not already launched, the notification data if any are stored in the key 'UIApplicationLaunchOptionsRemoteNotificationKey'
          NSDictionary *localLaunchOptions = [launchOptions objectForKey:@"UIApplicationLaunchOptionsRemoteNotificationKey"];
          if( localLaunchOptions )
          {
           ...
           [localLaunchOptions objectForKey:@"VAR"];
          ...
          }
     }
  }
  
  // Callback called when the application is already launched (whether the application is running foreground or background)
  - (void)application:(UIApplication *)application didReceiveRemoteNotification:(NSDictionary *)launchOptions
  {
      if( launchOptions )
      {
       ...
          [launchOptions objectForKey:@"VAR"];
      }
  }
  ```

>[!CAUTION]
>
>Adobe raadt u aan korte variabelenamen te kiezen, omdat de berichtgrootte voor iOS en Android beperkt is tot 4 kB.

+++

+++**Uitbreiding van de Dienst van het Bericht**

**voor iOS**

De media moeten worden gedownload op het niveau van de berichtdienst uitbreiding.

```
#import "NotificationService.h"

@interface NotificationService ()

@property (nonatomic, strong) void (^contentHandler)(UNNotificationContent *contentToDeliver);
@property (nonatomic, strong) UNMutableNotificationContent *bestAttemptContent;

@end

@implementation NotificationService

- (void)didReceiveNotificationRequest:(UNNotificationRequest *)request withContentHandler:(void (^)(UNNotificationContent * _Nonnull))contentHandler {
    NSDictionary *userInfo = nil;
    NSString *url = nil;

    self.contentHandler = contentHandler;
    self.bestAttemptContent = [request.content mutableCopy];

    userInfo = request.content.userInfo;
    if ( userInfo != nil )
    {
        url = userInfo[@"mediaUrl"];  // Get the url of the media to download (Adobe Campaign additional variable)
    }
    ...
    // Perform the download to local storage
```

+++

+++**de Uitbreiding van de Inhoud van het Bericht**

**voor iOS**

Op dit niveau moet u:

* Wijs de extensie van de inhoud toe aan de categorie die door Adobe Campaign is verzonden:

  Als u uw mobiele toepassing een beeld wilt tonen, kunt u de categoriewaarde aan &quot;beeld&quot;in Adobe Campaign en in uw mobiele toepassing plaatsen, creeert u een berichtuitbreiding met de **parameter 0&rbrace; UNNotificationExtensionCategory die aan &quot;beeld&quot;wordt geplaatst.** Wanneer het pushbericht op het apparaat wordt ontvangen, wordt de extensie aangeroepen op basis van de gedefinieerde categoriewaarde.

* De lay-out voor uw melding definiëren

  U moet een lay-out definiëren met de relevante widgets. Voor een beeld, wordt widget genoemd **UIImageView**.

* Uw media weergeven

  U moet code toevoegen om de mediagegevens aan de widget te kunnen doorgeven. Hier volgt een voorbeeld van code voor een afbeelding:

  ```
  #import "NotificationViewController.h"
  #import <UserNotifications/UserNotifications.h>
  #import <UserNotificationsUI/UserNotificationsUI.h>
  
  @interface NotificationViewController () <UNNotificationContentExtension>
  
  @property (strong, nonatomic) IBOutlet UIImageView *imageView;
  @property (strong, nonatomic) IBOutlet UILabel *notifContent;
  @property (strong, nonatomic) IBOutlet UILabel *label;
  
  @end
  
  @implementation NotificationViewController
  
  - (void)viewDidLoad {
      [super viewDidLoad];
      // Do any required interface initialization here.
  }
  
  - (void)didReceiveNotification:(UNNotification *)notification {
      self.label.text = notification.request.content.title;
      self.notifContent.text = notification.request.content.body;
      UNNotificationAttachment *attachment = [notification.request.content.attachments objectAtIndex:0];
      if ([attachment.URL startAccessingSecurityScopedResource])
      {
        NSData * imageData = [[NSData alloc] initWithContentsOfURL:attachment.URL];
        self.imageView.image =[UIImage imageWithData: imageData];
        [attachment.URL stopAccessingSecurityScopedResource];
      }
  }
  @end
  ```

+++
