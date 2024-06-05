---
product: campaign
title: 集成Campaign SDK
description: 了解如何将Campaign SDK集成到您的移动应用程序
feature: Mobile SDK Integration, Push
role: User, Developer
exl-id: a5f6b82d-5561-4e56-b2ed-7fd6fd8c2b55
source-git-commit: 00d46a7508def4d472e6bb8940a4d40a23c4fb07
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---

# 将Campaign SDK与您的应用程序集成 {#integrating-campaign-sdk-into-the-mobile-application}



>[!CAUTION]
>
>Adobe强烈建议通过在数据收集UI中配置Adobe Experience Platform扩展来使用Adobe Campaign Mobile SDK。 Adobe Experience Platform Mobile SDK有助于在移动设备应用程序中支持Adobe的Experience Cloud解决方案和服务。 SDK配置通过数据收集UI进行管理，以实现灵活配置和基于规则的可扩展集成。 [请参阅Adobe Developer文档以了解详情](https://developer.adobe.com/client-sdks/documentation/adobe-campaign-classic){target="_blank"}.

要获取Campaign SDK（以前称为Neolane SDK），请联系 [Adobe客户关怀](https://helpx.adobe.com/cn/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html){target="_blank"}.

要了解有关支持的各种Android和iOS版本的更多信息，请参阅 [兼容性矩阵](../../rn/using/compatibility-matrix.md#MobileSDK).

您可以在下面找到Campaign SDK的集成步骤。

+++**加载Campaign SDK**

* **在Android中**：和 **neolane_sdk-release.aar** 文件必须链接到项目。

  以下权限授予对Adobe Campaign服务器的访问权限：

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/");
  ```

  以下权限允许您恢复移动设备的唯一ID：

  ```
  <uses-permission android:name="android.permission.READ_PHONE_STATE" /> 
  ```

  从SDK版本1.0.24开始，此权限仅用于Android 6.0之前的版本。

  从SDK版本1.0.26开始，不再使用此权限。

* **在iOS中**：和 **libNeolaneSDK.a** 和 **Neolane_SDK.h** 文件必须链接到项目。 从SDK版本1.0.24开始，选项 **ENABLE_BITCODE** 已激活。

  >[!NOTE]
  >
  >对于SDK版本1.0.25，中提供了四种体系结构 **Neolane_SDK.h** 文件。

+++

+++**声明集成设置**

要将Campaign SDK集成到移动应用程序，功能管理员必须向开发人员提供以下信息：

* **集成密钥**：启用Adobe Campaign平台以标识移动应用程序。

  >[!NOTE]
  >
  >此集成键可在Adobe Campaign控制台中的以下位置输入： **[!UICONTROL Information]** 专用于移动应用程序的服务的选项卡。 请参阅 [在Adobe Campaign中配置移动应用程序](configuring-the-mobile-application.md).

* **跟踪URL**：与Adobe Campaign跟踪服务器的地址匹配。
* **营销URL**：启用订阅收藏集。

* **在Android中**：

  ```
  Neolane.getInstance().setIntegrationKey("your Adobe mobile app integration key");
  Neolane.getInstance().setMarketingHost("https://yourMarketingHost:yourMarketingPort/");
  Neolane.getInstance().setTrackingHost("https://yourTrackingHost:yourTrackingPort/"); 
  ```

* **在iOS中**：

  ```
  Neolane_SDK *nl = [Neolane_SDK getInstance];
  [nl setMarketingHost:strMktHost];
  [nl setTrackingHost:strTckHost];
  [nl setIntegrationKey:strIntegrationKey];
  ```

+++

+++**注册功能**

注册功能使您能够：

* 将通知ID或推送ID(iOS的deviceToken和Android的注册ID)发送到Adobe Campaign。
* 恢复协调密钥或userKey（例如，电子邮件或帐号）

* **在Android中**：

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

  如果您使用FCM(Firebase Cloud Messaging)，我们建议您使用 **registerDevice** 函数调用 **onTokenRefresh** 函数，用于在用户的移动设备令牌发生更改时通知Adobe Campaign。

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

* **在iOS中**：

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

+++**跟踪函数**

* **在Android中**：

  利用跟踪函数，可跟踪通知激活（打开）和通知显示（屏幕快照）。

  跟踪通知显示(通过调用 **notifyreceive** 函数)，请遵循以下实施。 请注意，如果您使用FCM(Firebase Cloud Messaging)，我们建议您使用 **notifyreceive** 函数当 **onMessageReceived** 函数由Android系统调用。

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

  以下是跟踪通知打开(通过调用 **notifyOpening** 函数)。 此 **通知活动** 类对应于用于创建 **notifIntent** 对象。

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

* **在iOS中**：

  跟踪函数允许您跟踪何时激活通知（打开）。

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
  >从版本7.0开始， **`application:didReceiveRemoteNotification:fetchCompletionHandler`** 函数实现，操作系统仅调用此函数。 此 **`application:didReceiveRemoteNotification`** 因此不调用函数。

+++

+++**静默通知跟踪**

iOS允许您发送静默通知、通知或数据，这些信息或数据将直接发送到移动应用程序，而不会显示通知。 Adobe Campaign允许您跟踪他们。

要跟踪静默通知，请按照以下示例操作：

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

+++**RegisterDeviceStatus委派**

>[!NOTE]
>
>请注意，这仅供iOS使用。

在iOS中，委派协议允许您获取 **registerDevice** 调用，并且可用于了解注册期间是否出现错误。

此 **registerDeviceStatus** 原型为：

```
- (void) registerDeviceStatus: (ACCRegisterDeviceStatus) status:(NSString *) errorReason;
```

**状态** 让您知道注册是否成功或发生错误。

**错误原因** 为您提供有关所发生错误的更多信息。 有关可用错误及其说明的更多信息，请参阅下表。

<table> 
 <thead>
  <tr>
   <th> 状态<br /> </th>
   <th> 说明<br /> </th>
   <th> 错误原因<br /> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td> ACCRegisterDeviceStatusSuccess <br /> </td>
   <td> 注册成功<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureMarketingServerHostnameEmpty <br /> </td>
   <td> ACC营销服务器主机名为空或未设置。<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureIntegrationKeyEmpty <br /> </td>
   <td> 集成键为空或未设置。<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureConnectionIssue<br /> </td>
   <td> 与ACC的连接问题<br /> </td>
   <td> 更多信息（以操作系统当前语言提供）<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnknownUUID<br /> </td>
   <td> 提供的UUID（集成密钥）未知。<br /> </td>
   <td> EMPTY<br /> </td>
  </tr>
  <tr> 
   <td> ACCRegisterDeviceStatusFailureUnexpectedError<br /> </td>
   <td> ACC服务器返回意外错误。<br /> </td>
   <td> 错误消息返回到ACC。<br /> </td>
  </tr>
 </tbody>
</table>

**Neolane_SDKDelegate** 协议和 **registerDeviceStatus** 委托定义如下：

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

实施 **registerDeviceStatus** 委派，请执行以下步骤：

1. 实施 **setDelegate** 在SDK初始化期间。

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

1. 将协议添加到 **@interface** 您班级的。

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

1. 在中实施委托 **AppDelegate**.

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

+++**变量**

利用变量，可定义在收到通知后的移动应用程序行为。 必须在移动设备应用程序代码以及Adobe Campaign控制台的中，定义这些变量 **[!UICONTROL Variables]** 选项卡(请参阅 [在Adobe Campaign中配置移动应用程序](configuring-the-mobile-application.md))。 下面是一个代码示例，该代码允许移动应用程序收集通知中添加的任何变量。 在我们的示例中，我们使用“VAR”变量。

* **在Android中**：

  ```
  public void onReceive(Context context, Intent intent) {
       ...
      String event = intent.getStringExtra("VAR");
       ...
  }
  ```

* **在iOS中**：

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
>Adobe建议选择短变量名称，因为对于iOS和Android，通知大小限制为4kB。

+++

+++**通知服务扩展**

**适用于iOS的**

介质必须在通知服务扩展级别下载。

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

+++**通知内容扩展**

**适用于iOS的**

在此级别，您需要：

* 将您的内容扩展关联到Adobe Campaign发送的类别：

  如果您希望移动设备应用程序显示图像，则可以在Adobe Campaign中将类别值设置为“图像”，并且在移动设备应用程序中，可以使用 **UNNotificationExtensionCategory** 参数设置为“image”。 当在设备上收到推送通知时，根据定义的类别值调用扩展。

* 定义通知布局

  您需要使用相关构件定义布局。 对于图像，将命名构件 **UImageView**.

* 显示您的媒体

  您需要添加代码以将媒体数据馈送到构件。 以下是图像的代码示例：

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
