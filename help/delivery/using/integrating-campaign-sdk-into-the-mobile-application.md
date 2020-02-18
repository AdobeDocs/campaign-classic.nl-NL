---
title: Mobiel app-kanaal instellen
seo-title: Mobiel app-kanaal instellen
description: Mobiel app-kanaal instellen
seo-description: null
page-status-flag: never-activated
uuid: aff1a4a0-34e7-4ce0-9eb3-30a8de1380f2
contentOwner: sauviat
products: SG_CAMPAIGN/CLASSIC
audience: delivery
content-type: reference
topic-tags: sending-push-notifications
discoiquuid: 7b5a1ad6-da5a-4cbd-be51-984c07c8d0b3
index: y
internal: n
snippet: y
translation-type: tm+mt
source-git-commit: a8c4face331ab6d646480322c0f53a7147251aa6

---


# Campagne SDK integreren in de mobiele toepassing {#integrating-campaign-sdk-into-the-mobile-application}

Campagne-SDK&#39;s voor iOS en Android zijn een van de onderdelen van de module Mobile App Channel.

>[!NOTE]
>
>Neem contact op met de klantenservice van Adobe om de Campagne SDK (voorheen bekend als Neolane SDK) op te halen.

Het doel van de SDK is om de integratie van een mobiele toepassing in het Adobe Campaign-platform te vergemakkelijken.

Raadpleeg de [compatibiliteitsmatrix](https://helpx.adobe.com/campaign/kb/compatibility-matrix.html#MobileSDK) voor meer informatie over de verschillende ondersteunde Android- en iOS-versies.

## Campagne SDK laden {#loading-campaign-sdk}

* **In Android**: het **bestand neolane_sdk-release.aar** moet aan het project zijn gekoppeld.

   Met de volgende machtigingen krijgt u toegang tot de Adobe Campagneserver:

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
   ```

   Met de volgende machtiging kunt u de unieke id van een telefoon herstellen:

   ```
   <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
   ```

   Vanaf versie 1.0.24 van de SDK wordt deze machtiging alleen gebruikt voor versies ouder dan Android 6.0.

   Vanaf versie 1.0.26 van de SDK wordt deze machtiging niet meer gebruikt.

* **In iOS**: de bestanden **libNeolaneSDK.a** en **Neolane_SDK.h** moeten aan het project zijn gekoppeld. Vanaf versie 1.0.24 van de SDK wordt de optie **ENABLE_BITCODE** geactiveerd.

   >[!NOTE]
   >
   >Voor versie 1.0.25 van de SDK zijn de vier architecturen beschikbaar in het bestand **Neolane_SDK.h** .

## Integratie-instellingen declareren {#declaring-integration-settings}

Als u de campagne-SDK wilt integreren in de mobiele toepassing, moet de functionele beheerder de ontwikkelaar de volgende informatie geven:

* **Een integratiesleutel**: om het Adobe Campagne-platform in staat te stellen de mobiele toepassing te identificeren.

   >[!NOTE]
   >
   >Deze integratietoets wordt ingevoerd in de Adobe Campagne Console, op het **[!UICONTROL Information]** tabblad Service dat is toegewezen aan de mobiele toepassing. Zie Een mobiele toepassing [configureren in Adobe Campagne](../../delivery/using/configuring-the-mobile-application.md).

* **Een URL** voor bijhouden: die overeenkomt met het adres van de Adobe Campagne Tracking-server.
* **Een marketing-URL**: om de inzameling van abonnementen toe te laten.

* **In Android**:

   ```
   Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
   Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
   Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
   ```

* **In iOS**:

   ```
   Neolane_SDK *nl = [Neolane_SDK getInstance];
   [nl setMarketingHost:strMktHost];
   [nl setTrackingHost:strTckHost];
   [nl setIntegrationKey:strIntegrationKey];
   ```

## Registratiefunctie {#registration-function}

Met de registratiefunctie kunt u:

* Stuur de bericht-id of push-id (deviceToken for iOS en registrationID for Android) naar Adobe Campagne.
* de afstemmingssleutel of de gebruikersnaam herstellen (bijvoorbeeld e-mail- of accountnummer)

* **In Android**:

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

   Als u FCM (Firebase Cloud Messaging) gebruikt, raden we u aan de functie **registerDevice** te gebruiken wanneer u de functie **onTokenRefresh** aanroept om Adobe Campaign op de hoogte te stellen van de wijziging in het token voor mobiele apparaten van de gebruiker.

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

* **In iOS**:

   ```
   // Callback called on successful registration to the APNS
   - (void)application:(UIApplication*)application didRegisterForRemoteNotificationsWithDeviceToken:(NSData*)deviceToken
   {
       // Pass the token to Adobe Campaign
       Neolane_SDK *nl = [Neolane_SDK getInstance];
       [nl registerDevice:tokenString:self.userKey:dic];
   }
   ```

## Traceerfunctie {#tracking-function}

* **In Android**:

   Met de trackingfuncties kunt u berichtactities (geopend) en berichtweergaven (screenshot) bijhouden.

   Volg de onderstaande implementatie om de berichtweergave bij te houden (uitgevoerd door de functie **notifyReceive** van de SDK aan te roepen). Als u FCM (Firebase Cloud Messaging) gebruikt, raden we u aan de functie **notifyReceive** te gebruiken wanneer de functie **onMessageReceived** door het Android-systeem wordt aangeroepen.

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

   Hier volgt een implementatievoorbeeld voor het bijhouden van een bericht dat is geopend (uitgevoerd door het aanroepen van de functie **notifyOpening** van de SDK). De **klasse NotificationActivity** komt overeen met de klasse die in het vorige voorbeeld is gebruikt om het **object notifyIntent** te maken.

   ```
   public class NotificationActivity extends Activity {
    public static final String NOTIFICATION_URL_KEYNAME = "NotificationUrl";
    .....
    public void onCreate(Bundle savedBundle) {
     super.onCreate(savedBundle);
     setContentView(R.layout.notification_viewer);  
     .....  
     Bundle extra = getIntent().getExtras();  
     .....  
     //get the messageId and the deliveryId to do the tracking  
     String deliveryId = extra.getString("_dId");
     String messageId = extra.getString("_mId");
     if (deliveryId != null && messageId != null) {
      NeolaneAsyncRunner neolaneAs = new NeolaneAsyncRunner(Neolane.getInstance());
      neolaneAs.notifyOpening(Integer.valueOf(messageId), deliveryId, new NeolaneAsyncRunner.RequestListener() {
       public void onNeolaneException(NeolaneException arg0, Object arg1) {}
       public void onIOException(IOException arg0, Object arg1) {}
       public void onComplete(String arg0, Object arg1) {}
       });
     }
    }
   }
   ```

* **In iOS**:

   Met de functie voor bijhouden kunt u bijhouden wanneer meldingen zijn geactiveerd (wordt geopend).

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
   >Vanaf versie 7.0 roept het besturingssysteem deze functie alleen aan als de functie **application:didReceiveRemoteNotification:fetchCompletionHandler** is geïmplementeerd. De functie **application:didReceiveRemoteNotification** wordt daarom niet aangeroepen.

## Beheer van stille meldingen {#silent-notification-tracking}

Met iOS kunt u geen meldingen verzenden, een melding of gegevens die rechtstreeks naar een mobiele toepassing worden verzonden zonder deze weer te geven. Met Adobe Campaign kunt u deze bijhouden.

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

### RegisterDeviceStatus-gedelegeerde {#registerdevicestatus-delegate}

>[!NOTE]
>
>Dit is exclusief voor iOS.

In iOS, staat het afgevaardigde protocol u toe om het resultaat van de vraag **registerDevice** te krijgen en kan worden gebruikt om te weten of een fout tijdens registratie voorkwam.

Het prototype **registerDeviceStatus** is:

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**Met Status** kunt u weten of een registratie is geslaagd of dat een fout is opgetreden.

**ErrorReason** verstrekt u van meer informatie over de fouten die voorkwamen. Raadpleeg de onderstaande tabel voor meer informatie over beschikbare fouten en beschrijvingen.

<table> 
 <thead>
  <tr>
   <th> Status<br /> </th>
   <th> Beschrijving<br /> </th>
   <th> ErrorReason<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> Registratie voltooid<br /> </td>
   <td> LEEG<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedMarketingServerHostnameEmpty <br /> </td>
   <td> De hostnaam van de ACC-marketingserver is leeg of niet ingesteld.<br /> </td>
   <td> LEEG<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedIntegrationKeyEmpty <br /> </td>
   <td> De integratietoets is leeg of niet ingesteld.<br /> </td>
   <td> LEEG<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedConnectionIssue<br /> </td>
   <td> Verbindingsprobleem met ACC<br /> </td>
   <td> Meer informatie (in huidige taal van besturingssysteem)<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedUnknownUID<br /> </td>
   <td> De opgegeven UUID (integratiesleutel) is onbekend.<br /> </td>
   <td> LEEG<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailedUnexpectedError<br /> </td>
   <td> Onverwachte fout die aan server ACC is teruggekeerd.<br /> </td>
   <td> The error message returned to ACC.<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** protocol en **registerDeviceStatus** gedelegeerde definitie is als volgt:

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

Voer de volgende stappen uit om **registerDeviceStatus** -gedelegeerde te implementeren:

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

1. Voeg het protocol in de **@interface** van uw klasse toe.

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

## Variabelen {#variables}

Met de variabelen kunt u het gedrag van mobiele toepassingen definiëren nadat u een melding hebt ontvangen. Deze variabelen moeten worden gedefinieerd in de code voor mobiele toepassingen en in de Adobe Campagne-console, op het **[!UICONTROL Variables]** tabblad in de toegewijde service voor mobiele toepassingen (zie Een mobiele toepassing [configureren in Adobe Campagne](../../delivery/using/configuring-the-mobile-application.md)). Hier is een voorbeeld van een code waarmee een mobiele toepassing toegevoegde variabelen in een melding kan verzamelen. In ons voorbeeld gebruiken we de variabele &quot;VAR&quot;.

* **In Android**:

   ```
   public void onReceive(Context context, Intent intent) {
        ...
       String event = intent.getStringExtra("VAR");
        ...
   }
   ```

* **In iOS**:

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

## Meldingsservice-extensie {#notification-service-extension}

**Voor iOS**

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

## Extensie meldingsinhoud {#notification-content-extension}

**Voor iOS**

Op dit niveau moet u:

* Wijs de extensie van de inhoud toe aan de categorie die wordt verzonden door Adobe Campaign:

   Als u wilt dat uw mobiele toepassing een afbeelding weergeeft, kunt u de categoriewaarde instellen op &quot;image&quot; in Adobe Campagne en in uw mobiele toepassing. U maakt dan een meldingsextensie met de parameter **UNNotificationExtensionCategory** ingesteld op &quot;image&quot;. Wanneer het pushbericht op het apparaat wordt ontvangen, wordt de extensie aangeroepen op basis van de gedefinieerde categoriewaarde.

* De lay-out voor uw melding definiëren

   U moet een lay-out definiëren met de relevante widgets. Voor een afbeelding krijgt de widget de naam **UIImageView**.

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
