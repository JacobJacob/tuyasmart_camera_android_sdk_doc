# Cloud storage purchase H5 components



## Introduction

This component provides H5 pages and order display functions for cloud storage purchases



## Import

1. Build.gradle in the project root：

```groovy
buildscript {
    ···
    dependencies {
        classpath 'com.android.tools.build:gradle:3.1.4'
        classpath 'com.tuya.android.module:tymodule-config:0.4.0-SNAPSHOT'
    }
}

```

2. Build.gradle of the project module：

```groovy
apply plugin: 'tymodule-config'

...
implementation 'com.tuya.smart:tuyasmart-webcontainer:3.12.6r125'
implementation 'com.tuya.smart:tuyasmart-xplatformmanager:1.1.0'
implementation "com.tuya.smart:tuyasmart-base:3.13.0r127"
implementation 'com.tuya.smart:tuyasmart-appshell:3.10.0'
implementation "com.tuya.smart:tuyasmart-stencilwrapper:3.13.0r127"
implementation "com.tuya.smart:tuyasmart-framework:3.13.0r127-open-rc.1"
implementation 'com.tuya.smart:tuyasmart-uispecs:0.0.3'
```



## Use

**Sample Code**

Styles.xml needs to be modified

```xml

<!-- Base application theme. -->
<style name="AppTheme" parent="Theme.AppCompat.NoActionBar">
  <!-- Customize your theme here. -->
  <item name="colorPrimary">@color/colorPrimary</item>
  <item name="colorPrimaryDark">@color/colorPrimaryDark</item>
  <item name="colorAccent">@color/colorAccent</item>
  <item name="android:windowBackground">@color/window_bg</item>
</style>

<style name="SplashTheme" parent="AppTheme">
  <item name="android:windowBackground">@drawable/ty_pre</item>
</style>

<style name="edit_text_input">
  <item name="android:layout_width">match_parent</item>
  <item name="android:layout_height">@dimen/edit_height</item>
  <item name="android:background">@null</item>
  <item name="android:paddingRight">10dp</item>
  <item name="android:gravity">center_vertical</item>
  <item name="android:textCursorDrawable">@null</item>
  <item name="android:textSize">15sp</item>
  <item name="android:singleLine">true</item>
  <item name="android:textColorHint">?attr/list_secondary_color</item>
  <item name="android:textColor">?attr/list_primary_color</item>
</style>

<style name="TY_SingleLine_Normal">
  <item name="android:layout_height">1px</item>
  <item name="android:layout_width">match_parent</item>
  <item name="android:background">@color/line_color</item>
</style>

<style name="Button.Normal" parent="android:Widget.Button">
  <item name="android:layout_height">@dimen/wh_36</item>
  <item name="android:minWidth">@dimen/wh_88</item>
  <item name="android:layout_width">wrap_content</item>
  <item name="android:singleLine">true</item>
  <item name="android:textSize">@dimen/ts_18</item>
  <item name="android:textStyle">normal</item>
  <item name="android:ellipsize">end</item>
  <item name="android:background">@drawable/button_orange</item>
  <item name="android:textColor">@color/button_orange_text</item>
</style>

<style name="TY.Progress.Dialog" parent="Theme.AppCompat.Dialog">
  <item name="colorAccent">@color/color_accent</item>
  <item name="android:lineSpacingExtra">@dimen/wh_4</item>
</style>


<style name="TY_List_Normal">
  <item name="android:fadingEdge">none</item>
  <item name="android:listSelector">@android:color/transparent</item>
  <item name="android:divider">@color/line_color</item>
  <item name="android:dividerHeight">@dimen/single_pix</item>
  <item name="android:listDivider">@drawable/ty_color_line</item>
  <item name="android:footerDividersEnabled">false</item>
  <item name="android:cacheColorHint">@android:color/transparent</item>
  <item name="android:scrollbarThumbVertical">@drawable/ty_scrollbar_thumb</item>
  <item name="android:scrollbarTrackVertical">@null</item>
</style>


<style name="toolbar_menu_text" parent="Theme.AppCompat.Light.DarkActionBar">
  <item name="android:textSize">17sp</item>
  <item name="android:textStyle">bold</item>
</style>


<style name="AppTheme.Base" parent="Theme.AppCompat.NoActionBar">
  <!-- colorPrimary is used for the default action bar background -->
  <item name="colorPrimary">?attr/status_bg_color</item>
  <!-- colorPrimaryDark is used for the status bar -->
  <item name="colorPrimaryDark">?attr/status_bg_color</item>
  <!-- colorAccent is used as the default value for colorControlActivated,
              which is used to tint widgets -->
  <item name="colorAccent">@color/color_accent</item>

  <item name="android:textColorPrimary">@color/white</item>
  <item name="android:windowBackground">@drawable/ty_pre</item>


  <item name="android:windowContentOverlay">@android:color/transparent</item>

  <item name="android:windowFullscreen">false</item>

  <!-- You can also set colorControlNormal, colorControlActivated
            colorControlHighlight, and colorSwitchThumbNormal. -->
  <!--<item name="actionButtonStyle">@color/colorMenu</item>-->
  <!--<item name="android:actionButtonStyle">@color/colorMenu</item>-->
  <item name="android:colorBackgroundCacheHint">@android:color/transparent</item>

  <item name="android:popupBackground">@color/color_primary</item>

  <item name="android:windowAnimationStyle">@style/noAnimation</item>

  <item name="android:actionMenuTextColor">@color/white</item>
  <item name="android:actionMenuTextAppearance">@style/toolbar_action_text</item>
  <item name="actionModeBackground">@color/color_primary</item>

  <item name="colorSwitchThumbNormal">@color/gray</item>
  <item name="android:colorForeground">@color/gray_70</item>

  <item name="actionMenuTextColor">?attr/status_font_color</item>
</style>
<style name="noAnimation">
  <item name="android:activityOpenEnterAnimation">@null</item>
  <item name="android:activityOpenExitAnimation">@null</item>
  <item name="android:activityCloseEnterAnimation">@null</item>
  <item name="android:activityCloseExitAnimation">@null</item>
  <item name="android:taskOpenEnterAnimation">@null</item>
  <item name="android:taskOpenExitAnimation">@null</item>
  <item name="android:taskCloseEnterAnimation">@null</item>
  <item name="android:taskCloseExitAnimation">@null</item>
  <item name="android:taskToFrontEnterAnimation">@null</item>
  <item name="android:taskToFrontExitAnimation">@null</item>
  <item name="android:taskToBackEnterAnimation">@null</item>
  <item name="android:taskToBackExitAnimation">@null</item>
</style>

<style name="MyMenuTextAppearance" parent="android:TextAppearance.Holo.Widget.ActionBar.Menu">

  <item name="android:textAllCaps">false</item>
</style>


<style name="TextView.Normal" parent="android:Widget.TextView">
  <item name="android:textSize">@dimen/ts_15</item>
  <item name="android:textColor">@color/textColor</item>
  <item name="android:lineSpacingExtra">4dp</item>
  <item name="android:ellipsize">end</item>
</style>

<style name="ProgressBar.Normal" parent="Widget.AppCompat.ProgressBar">
  <item name="android:minWidth">23dp</item>
  <item name="android:maxWidth">23dp</item>
  <item name="android:minHeight">23dp</item>
  <item name="android:maxHeight">23dp</item>
  <item name="android:textColor">@color/color_626262</item>
</style>


<!-- list view-->
<style name="list_view">
  <item name="android:layout_width">match_parent</item>
  <item name="android:layout_height">wrap_content</item>
  <item name="android:background">?attr/list_bg_color</item>
  <item name="android:divider">@null</item>
  <item name="android:dividerHeight">0dp</item>
  <item name="android:clickable">true</item>
  <item name="android:descendantFocusability">blocksDescendants</item>
</style>



<style name="line_long">
  <item name="android:layout_width">match_parent</item>
  <item name="android:layout_height">@dimen/line_dip</item>
  <item name="android:background">@color/list_line_color</item>
</style>
<style name="dialog_style" parent="android:Animation">
  <item name="android:windowEnterAnimation">@anim/dialog_enter</item>

  <item name="android:windowExitAnimation">@anim/dialog_exit</item>

</style>

<style name="dialog_alert" parent="@android:style/Theme.Holo.DialogWhenLarge">
  <item name="android:windowNoTitle">true</item>
  <item name="android:windowBackground">@android:color/transparent</item>
  <item name="android:windowFrame">@null</item>
</style>

<style name="SampleTheme" parent="android:Theme">
  <item name="numberPickerStyle">@style/NPWidget.Holo.NumberPicker</item>
</style>
<style name="NPWidget.Holo.NumberPicker" parent="NPWidget.NumberPicker">
  <item name="solidColor">@android:color/transparent</item>
  <item name="selectionDivider">@null</item>
  <item name="selectionDividerHeight">1dip</item>
  <item name="internalLayout">@layout/number_picker_with_selector_wheel</item>
  <item name="internalMinWidth">64dip</item>
  <item name="internalMaxHeight">180dip</item>
</style>

<style name="NPWidget.NumberPicker">
  <item name="android:orientation">vertical</item>
  <item name="android:fadingEdge">vertical</item>
  <item name="android:fadingEdgeLength">50dip</item>
</style>
<style name="NPWidget">
  <item name="android:textAppearance">?android:attr/textAppearance</item>
</style>


<style name="ListItem.ItemNormal" parent="android:Widget">
  <item name="android:layout_height">48dp</item>
  <item name="android:layout_width">match_parent</item>
  <item name="android:paddingLeft">16dp</item>
  <item name="android:paddingRight">16dp</item>
  <item name="android:paddingTop">@dimen/ts_12</item>
  <item name="android:paddingBottom">@dimen/ts_12</item>
  <item name="android:gravity">center_vertical|right</item>
  <item name="android:textColor">@color/text_color</item>
</style>


<style name="Dialog.Alert.NoTitle" parent="@style/Dialog.Alert">
  <item name="android:windowNoTitle">true</item>
</style>

<style name="Dialog.Alert" parent="Theme.AppCompat.Light.Dialog.Alert">
  <item name="colorAccent">@color/color_accent</item>
  <item name="android:lineSpacingExtra">@dimen/wh_4</item>
</style>

<style name="Dialog.Alert.Multichoice" parent="@style/Dialog.Alert">
  <!--<item name="android:listChoiceIndicatorMultiple">@null</item>-->
</style>

<style name="Dialog.Alert.Singlechoice" parent="@style/Dialog.Alert">
  <!--<item name="android:listChoiceIndicatorSingle">@null</item>-->
</style>

<style name="ToolBarStyle" parent="ToolBarStyle.Base"/>

<style name="ToolBarStyle.Base" parent="">
  <item name="popupTheme">@style/ThemeOverlay.AppCompat.Light</item>
  <item name="theme">@style/ThemeOverlay.AppCompat.Dark.ActionBar</item>
  <item name="titleTextAppearance">@style/myActionTitleTextAppearance</item>
</style>


<style name="line_normal">
  <item name="android:layout_width">match_parent</item>
  <item name="android:layout_height">@dimen/line_dip</item>
  <item name="android:background">@color/line</item>
</style>

<style name="myActionTitleTextAppearance"
       parent="@style/TextAppearance.AppCompat.Widget.ActionBar.Menu">
  <item name="android:textSize">@dimen/tuya_title_size</item>
  <item name="android:textStyle">normal</item>
  <item name="android:textColor">@color/white</item>
  <item name="android:textAllCaps">false</item>
</style>

<style name="EditText.Normal" parent="android:Widget.EditText">
  <item name="android:background">@drawable/bg_white_round</item>
  <item name="android:textSize">@dimen/ts_16</item>
  <item name="android:textColor">@color/text_color</item>
  <item name="android:textColorHint">@color/text_hint_color</item>
  <item name="android:layout_height">wrap_content</item>
  <item name="android:layout_width">match_parent</item>
  <item name="android:gravity">center_vertical|left</item>
  <item name="android:singleLine">true</item>
  <item name="android:ellipsize">end</item>
  <item name="android:maxLength">64</item>
  <item name="android:textCursorDrawable">@drawable/cursor_orange</item>
</style>

<style name="Default_Public_Theme" parent="AppTheme">

  <item name="status_font_color">@color/app_bg_color</item>
  <item name="status_bg_color">@color/navbar_font_color</item>
  <item name="status_system_bg_color">@color/status_system_bg_color</item>
  <item name="navbar_font_color">@color/navbar_font_color</item>
  <item name="navbar_bg_color">@color/navbar_font_color</item>
  <item name="app_bg_color">@color/app_bg_color</item>
  <item name="fragment_bg_color">@color/app_bg_color</item>

  <item name="list_primary_color">@color/list_primary_color</item>
  <item name="list_sub_color">@color/list_sub_color</item>
  <item name="list_secondary_color">@color/list_secondary_color</item>
  <item name="list_line_color">@color/list_line_color</item>
  <item name="list_bg_color">@color/list_bg_color</item>
  <item name="notice_font_color">@color/notice_font_color</item>
  <item name="notice_bg_color">@color/notice_bg_color</item>

  <item name="primary_button_font_color">@color/primary_button_font_color</item>
  <item name="primary_button_bg_color">@color/primary_button_bg_color</item>
  <item name="secondary_button_font_color">@color/secondary_button_font_color</item>
  <item name="secondary_button_bg_color">@color/secondary_button_bg_color</item>

  <item name="app_name">@string/app_name</item>
  <item name="login_flow">0</item>
  <item name="package_mode">0</item>

  <item name="bg_normal_text_bt">@drawable/bg_text_bts</item>

  <item name="language_mode">0</item>
  <item name="android:windowBackground">@color/status_bg_color</item>
  <item name="android:windowIsTranslucent">false</item>
  <item name="actionBarSize">@dimen/abc_action_bar_default_height_material</item>
  <item name="is_add_device_help_get_from_native">false</item>
  <item name="is_scene_support">true</item>
</style>
<style name="ToolrTheme" parent="Default_Public_Theme">
  <item name="status_font_color">@color/white</item>
  <item name="status_bg_color">@color/color_ff5800</item>
  <item name="app_bg_color">@color/color_ff5800</item>
</style>
<style name="Splash.Theme" parent="Default_Public_Theme">
  <item name="android:windowBackground">@drawable/ty_pre</item>
</style>


<color name="color_ff5800">#ff5800</color>
```

application initialization

  ```java
public class TuyaSmartApp extends MultiDexApplication {

  private static final String TAG = "TuyaSmartApp";

  @Override
  public void onCreate() {
    super.onCreate();
    context=this;
    L.d(TAG, "onCreate " + getProcessName(this));
    L.setSendLogOn(true);
    TuyaWrapper.init(this);
    TuyaSdk.init(this);
    ...
  }

  ```

Jump to cloud storage purchase page

```java
findViewById(R.id.buy_btn).setOnClickListener(new View.OnClickListener() {
  @Override
  public void onClick(View v) {
    cameraCloudSDK.buyCloudStorage(CameraCloudStorageActivity.this,
                                   TuyaHomeSdk.getDataInstance().getDeviceBean(devId),
                                   String.valueOf(FamilyManager.getInstance().getCurrentHomeId()), new ICloudManagerCallback() {
                                     @Override
                                     public void onError(int i) {

                                     }

                                     @Override
                                     public void onSuccess(Object o) {
                                       String uri = (String) o;
                                       Intent intent = new Intent(CameraCloudStorageActivity.this, WebViewActivity.class);
                                       intent.putExtra("Uri",uri);
                                       startActivity(intent);
                                     }
                                   });
  }
});
```

