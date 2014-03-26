// Screenshot を撮る
Application.CaptureScreenshot("screenshot.png");

// プラットフォームごとに保存位置変わる？
string path = "";
switch (Application.platform) {
	case RuntimePlatform.IPhonePlayer:
		path = Application.persistentDataPath + "/screenshot.png";
		break;
	case RuntimePlatform.Android:
		path = Application.persistentDataPath + "/screenshot.png";
		break;
	default:
		path = "screenshot.png";
		break;
}
Debug.Log("path:"+path);

// スクリーンショットの読み込み
byte[] image = File.ReadAllBytes(path);

// Texture2D を作成して読み込み
Texture2D tex = new Texture2D(0, 0);
tex.LoadImage(image);

// NGUI の UITexture に表示するとき
UITexture target = GameObject.Find("DebugTexture").GetComponent();
target.mainTexture = tex;