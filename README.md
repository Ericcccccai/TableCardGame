# TableCardGame
This web app demonstrates different card games and you may be able to purchase some card games too. 

Front-End:
  - Html
  - CSS
  - JavaScript (React Native)
  - Later in the mobile app, Flutter

Back-End:
  - Java
  - Go MAYBE

Database:
  - MySQL

Cloud:
  - AWS


MORE TO DISCOVER





Windows 11 instructions:
My version: 2022.3.2f1 LTS


- Open the project with this version on Unity Hub (choose the safe mode when asked). 
- There should be about 29 warnings and 13 errors. 
- These errors are mainly because of the Unity update that changed the hey word `GUIText` to `Text` and `GUITexture` to `Image`.
- If not included, add `using UnityEngine.UI;` to the top of the file.
- Double-click on the error to open the error file, and replace the keywords.
- Some other errors:
   - Assets\JMO Assets\Cartoon FX\Demo\UI\CFX_Demo_GTToggle.cs
      - Update `public Texture Normal, Hover`; to ` public Sprite Hover;` `public Sprite Normal;`
      - Update the function awake() to 
         - RectTransform rectTransform=GetComponent<RectTransform>();
         - Vector3[] corners = new Vector3[4];
         - rectTransform.GetWorldCorners(corners);
         -          - // Bottom-left corner of the rect in screen space
         - Vector3 screenBottomLeft = RectTransformUtility.WorldToScreenPoint(Camera.main, corners[0]);
         -          - // Top-right corner of the rect in screen space
         - Vector3 screenTopRight = RectTransformUtility.WorldToScreenPoint(Camera.main, corners[2]);
         -          - // Create a Rect from the bottom-left and top-right corners
         - CollisionRect = Rect.MinMaxRect(screenBottomLeft.x, screenBottomLeft.y, screenTopRight.x, screenTopRight.y);
         -          - Label = this.GetComponentInChildren<Text>();
         -          - UpdateTexture();
      - Update the function UpdateTexture() to
         - Color col = State ? NormalColor : DisabledColor;
         - Image imageComponent = this.GetComponent<Image>();
         -          - if (Over){
         - imageComponent.sprite = Hover;
         - }else{
         - imageComponent.sprite = Normal;
         - }
         - imageComponent.color = col;
         -          - if (Label != null)
         - Label.color = col - 1.75f;
   - Assets\Toon Character Pack\Toon Animations\ToonAnimations.cs
      - Update the last if statement in function OnGUI() to
         - if (image != null){
         - RectTransform rectTransform = image.GetComponent<RectTransform>();
         -          -      if (rectTransform != null && image.sprite != null){
         -      var tmp_cs1 = rectTransform.anchoredPosition;
         -      tmp_cs1.x = (float)(Screen.width - image.sprite.rect.width) / 2f;
         -      rectTransform.anchoredPosition = tmp_cs1;
         -      }
         - }
   - Assets\Toon Character Pack\Scripts\GameObjectSpawner_Characters.cs
      - Update the error if statement to the same as above
- After these 13 errors are fixed, there should be popping up 8 new errors with 172 warnings.
   - Assets\David\Fungus\Thirdparty\Usfxr\Scripts\SfxrAudioPlayer.cs(55,26): error CS1729: 'AudioClip' does not contain a constructor that takes 0 arguments
      - Update `soundSource.clip = new AudioClip();` to `soundSource.clip = null;`
   - Assets\JMO Assets\Cartoon FX\Demo\UI\CFX_Demo_GTButton.cs
      - Update function Awake() to:
         - RectTransform rectTransform=this.GetComponent<RectTransform>();
         -                 if (rectTransform != null){
         -                         Rect rect = new Rect(
         -                                 rectTransform.position.x,
         -                                 rectTransform.position.y,
         -                                 rectTransform.rect.width,
         -                                 rectTransform.rect.height
         -                         );
         -          -                         CollisionRect = rect;
         -                 }
      - Update function Update() to:
         - Image imageComponent = this.GetComponent<Image>();
         -                 if (imageComponent != null){
         -                         RectTransform rectTransform = this.GetComponent<RectTransform>();
         -                         if (rectTransform != null){
         -                                 Rect rect = new Rect(
         -                                         rectTransform.position.x,
         -                                         rectTransform.position.y,
         -                                         rectTransform.rect.width,
         -                                         rectTransform.rect.height
         -                                 );
         -          -                         if(rect.Contains(Input.mousePosition)){
         -                         imageComponent.color = HoverColor;
         -          -                                 if(Input.GetMouseButtonDown(0)){
         -                                         OnClick();
         -                                         }
         -                                 }else{
         -                                         imageComponent.color =  NormalColor;
         -                                 }
         -                         }
         -                 }
      - Update the error if statement to:
         - if (!((r is TrailRenderer) || (r is ParticleSystemRenderer)))
   - After fixing these errors, a new error should be popped up
      - Assets\PostProcessing\Editor\PropertyDrawers\MinDrawer.cs
      - Update `MinAttribute` to `UnityEngine.PostProcessing.MinAttribute`
   - After the previous error is fixed, one more error should be popped up
      - Assets\Heureka\AssetHunterPRO\Editor\Scripts\AH_Utils.cs(282,79): error CS0619: 'PlayerSettings.WSA.packageLogo' is obsolete: 'Use GetVisualAssetsImage()/SetVisualAssetsImage()'
      - Update line 282 to `textures.Add(AssetDatabase.LoadAssetAtPath<Texture2D>(PlayerSettings.WSA.GetVisualAssetsImage(PlayerSettings.WSAImageType.PackageLogo, PlayerSettings.WSAImageScale._100)));`
   - Now the Unity edit page should be showing up, and about 124 warnings and 20 errors. 
   - Close and restart the project. After restart, there should be no errors and only 8 warnings.
   - Make sure to have Android 11.0 (API Level 30) installed. You can do this through SDK Manager in Android Studio. Also in the SDK manager, under the SDK tool, make sure to have Android SDK Command-line Tools installed too. 
   - Go to preferences (under edit), and update the Android SDK Tool location. Finding the location of the SDK should be automatic if the previous step is correctly done.
   - Go to Build Settings (under File), and switch the platform to Android. 
   - Under Player Setting, download the Keystore. Please ask Ethan for the download info. Update the Keystore path and update the Project Key. 
   - Under other settings, change the Minimum and Target API Level to Android 11.0 (API Level 30)
   - Under Assets\Plugins\Android, find luncherTemplate.gradle and mainTemplate.gradle.
      - Update the old noCompress to `noCompress = ['.unity3d', '.ress', '.resource', '.obb'].concat(unityStreamingAssets)`
      - Delete the lines with `useProguard` and `proguardFiles` under buildTypes\debug and release
        -        Now, you should be able to build the project and create a .apk file. 




Windows 11 教程：
我的版本：2022.3.2f1 LTS


- 使用此版本在Unity Hub上打开项目（如果询问，请选择安全模式）。
- 应该会有大约29个警告和13个错误。
- 这些错误主要是由于Unity更新将关键词`GUIText`更改为`Text`，`GUITexture`更改为`Image`。
- 如果没写，请在文件顶部添加`using UnityEngine.UI;`。
- 双击错误以打开错误文件，并替换关键词。
- 其他一些错误：
   - Assets\JMO Assets\Cartoon FX\Demo\UI\CFX_Demo_GTToggle.cs
   - 更新 `public Texture Normal, Hover;` 为`public Sprite Hover;` `public Sprite Normal;`
   - 更新函数awake()为
      - RectTransform rectTransform=GetComponent<RectTransform>();
      - Vector3[] corners = new Vector3[4];
      - rectTransform.GetWorldCorners(corners);
      -       - // Bottom-left corner of the rect in screen space
      - Vector3 screenBottomLeft = RectTransformUtility.WorldToScreenPoint(Camera.main, corners[0]);
      -       - // Top-right corner of the rect in screen space
      - Vector3 screenTopRight = RectTransformUtility.WorldToScreenPoint(Camera.main, corners[2]);
      -       - // Create a Rect from the bottom-left and top-right corners
      - CollisionRect = Rect.MinMaxRect(screenBottomLeft.x, screenBottomLeft.y, screenTopRight.x, screenTopRight.y);
      -       - Label = this.GetComponentInChildren<Text>();
      -       - UpdateTexture();
   - 更新函数UpdateTexture()为
      - Color col = State ? NormalColor : DisabledColor;
      - Image imageComponent = this.GetComponent<Image>();
      - if (Over){
      - imageComponent.sprite = Hover;
      - }else{
      - imageComponent.sprite = Normal;
      - }
      - imageComponent.color = col;
      - if (Label != null)
      - Label.color = col - 1.75f;
   - Assets\Toon Character Pack\Toon Animations\ToonAnimations.cs
   - 更新函数OnGUI()中最后的if语句为：
      - if (image != null){
      - RectTransform rectTransform = image.GetComponent<RectTransform>();
      -       -      if (rectTransform != null && image.sprite != null){
      -      var tmp_cs1 = rectTransform.anchoredPosition;
      -      tmp_cs1.x = (float)(Screen.width - image.sprite.rect.width) / 2f;
      -      rectTransform.anchoredPosition = tmp_cs1;
      -      }
      - }
   - Assets\Toon Character Pack\Scripts\GameObjectSpawner_Characters.cs
   - 将错误的if语句更新为上述内容
- 修复这13个错误后，应该会弹出8个新错误，和172个警告。
   - Assets\David\Fungus\Thirdparty\Usfxr\Scripts\SfxrAudioPlayer.cs(55,26): error CS1729: 'AudioClip' does not contain a constructor that takes 0 arguments
      - 更新`soundSource.clip = new AudioClip();`为`soundSource.clip = null;`
   - Assets\JMO Assets\Cartoon FX\Demo\UI\CFX_Demo_GTButton.cs
   - 更新函数Awake()为:
      - RectTransform rectTransform=this.GetComponent<RectTransform>();
      -                 if (rectTransform != null){
      -                         Rect rect = new Rect(
      -                                 rectTransform.position.x,
      -                                 rectTransform.position.y,
      -                                 rectTransform.rect.width,
      -                                 rectTransform.rect.height
      -                         );
      -       -                         CollisionRect = rect;
      -                 }
   - 更新函数Update()为:
      - Image imageComponent = this.GetComponent<Image>();
      -                 if (imageComponent != null){
      -                         RectTransform rectTransform = this.GetComponent<RectTransform>();
      -                         if (rectTransform != null){
      -                                 Rect rect = new Rect(
      -                                         rectTransform.position.x,
      -                                         rectTransform.position.y,
      -                                         rectTransform.rect.width,
      -                                         rectTransform.rect.height
      -                                 );
      -                                if(rect.Contains(Input.mousePosition)){
      -                                  imageComponent.color = HoverColor;
      -                                        if(Input.GetMouseButtonDown(0)){
      -                                         OnClick();
      -                                         }
      -                                 }else{
      -                                         imageComponent.color =  NormalColor;
      -                                 }
      -                         }
      -                 }
   - 将错误的if语句更新为：
      - if (!((r is TrailRenderer) || (r is ParticleSystemRenderer)))
- 修复这些错误后，应该会弹出一个新错误
   - Assets\PostProcessing\Editor\PropertyDrawers\MinDrawer.cs
   - 更新`MinAttribute`为`UnityEngine.PostProcessing.MinAttribute`
- 修复上述错误后，应该会弹出一个新错误
   - Assets\Heureka\AssetHunterPRO\Editor\Scripts\AH_Utils.cs(282,79): error CS0619: 'PlayerSettings.WSA.packageLogo' is obsolete: 'Use GetVisualAssetsImage()/SetVisualAssetsImage()'
   - 将第282行更新为`textures.Add(AssetDatabase.LoadAssetAtPath<Texture2D>(PlayerSettings.WSA.GetVisualAssetsImage(PlayerSettings.WSAImageType.PackageLogo, PlayerSettings.WSAImageScale._100)));`
- 此时Unity编辑页面应该显示大约124个警告和20个错误。
- 关闭并重新启动项目。重启后，应该没有错误，只有8个警告。
- 确保已安装Android 11.0（API级别30）。您可以通过Android Studio中的SDK Manager完成此操作。同时在SDK Manager的SDK工具下，确保已安装Android SDK命令行工具。
- 在偏好设置里，并更新Android SDK工具位置。如果前一步骤正确完成，SDK的位置应该是自动找到的。
- 转到构建设置，并将平台切换到Android。
- 在玩家设置下，更新Keystore。请向Ethan询问下载信息。更新Keystore路径并更新项目密钥。
- 在其他设置下，将最小和目标API级别更改为Android 11.0（API级别30）
- 在Assets\Plugins\Android下，找到luncherTemplate.gradle和mainTemplate.gradle。
   - 将旧的noCompress更新为`noCompress = ['.unity3d', '.ress', '.resource', '.obb'].concat(unityStreamingAssets)`
   - 在同一文件里删除buildTypes\debug和release下带有`useProguard`和`proguardFiles`的行
- 现在，您应该能够构建项目并创建.apk文件。
