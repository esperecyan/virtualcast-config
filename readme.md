VirtualCast/config.yaml
=======================
`プロファイル名_config.yaml` (または `プロファイル名_config.yml`) を `プロファイル名_config.json` へ変換後、VirtualCastを起動する[WSH]スクリプトです。

[WSH]: https://ja.wikipedia.org/wiki/Windows_Script_Host "Windows Script Hostとは、Microsoft Windowsにおいてテキストファイルに記述したスクリプトを実行するスクリプト実行環境である。"

例
---
`VirtualCast.exe` があるフォルダに次のような `プロファイル名_config.yaml` を置いておくと、

```yaml
panorama:
    urls: # 背景で使うパノラマ画像のURL
        - 'https://www.virtualcast.jp/download/panoramas/IL_entrance.JPG'
        - 'https://www.virtualcast.jp/download/panoramas/chromakey.jpg'
        - 'https://www.virtualcast.jp/download/panoramas/chromakey_white.jpg'
whiteboard:
    urls: # ホワイトボードで使用する画像のURL
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-red-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-blue-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-pop-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-sd-1024x768.jpg'
cue_card:
    urls: # カンペで使用する画像のURL
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-red-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-blue-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-pop-1024x768.jpg'
        - 'https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-sd-1024x768.jpg'
# ダイレクトビューモードで凸を受け入れるかどうか
allow_direct_view: true
```

次のような `プロファイル名_config.json` に変換されます。

```json
{
	"panorama": {
		"urls": [
			"https://www.virtualcast.jp/download/panoramas/IL_entrance.JPG",
			"https://www.virtualcast.jp/download/panoramas/chromakey.jpg",
			"https://www.virtualcast.jp/download/panoramas/chromakey_white.jpg"
		]
	},
	"whiteboard": {
		"urls": [
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-red-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-blue-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-pop-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-sd-1024x768.jpg"
		]
	},
	"cue_card": {
		"urls": [
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-red-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-blue-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-pop-1024x768.jpg",
			"https://www.infiniteloop.co.jp/special/iltan/kabegami/infiniteloop-iltan-sd-1024x768.jpg"
		]
	},
	"allow_direct_view": true
}
```

使い方
------
![](demo.gif)

1. [バーチャルキャストを起動.js]を好きなフォルダに保存します。
2. `バーチャルキャストを起動.js` をダブルクリックして実行します。
3. `default_config.json` の内容をもとに `default_config.yaml` が作成された後、バーチャルキャストが起動します。
4. `default_config.yaml` が存在する場合、変換して `default_config.json` に上書き保存され、その後バーチャルキャストが起動します。
5. `VirtualCast.exe` を直接起動する代わりに、常に `バーチャルキャストを起動.js` からバーチャルキャストを起動するようにしておくと、
   `default_config.json` の更新を意識せずにすむため便利です。

[バーチャルキャストを起動.js]: https://esperecyan.github.io/virtualcast-config/%E3%83%90%E3%83%BC%E3%83%81%E3%83%A3%E3%83%AB%E3%82%AD%E3%83%A3%E3%82%B9%E3%83%88%E3%82%92%E8%B5%B7%E5%8B%95.js

起動オプション
--------------
### `--esperecyan-disable-eye-lip-tracking`
VIVEのアイトラッキング、リップトラッキングを無効化します。

JSONへの変換時に次のプロパティを削除します。
- `enable_vivesranipal_eye`
- `enable_vivesranipal_blink`
- `enable_vivesranipal_eye_with_emotion`
- `enable_vivesranipal_lip`

VirtualCast 2.1.5e (2022-01-20) 現在、VIVE Pro Eye以外を接続している場合、VIVEのアイトラッキングを有効にしていると、VirtualCastがフリーズし、OSの再起動が必要になる不具合があります。
https://virtualcast.jp/blog/2022/01/0126_shinchoku/

### `--esperecyan-document-index=[数字]` (0から始まる整数)
一つのファイル内に複数のYAMLドキュメントが埋め込まれていた場合、読み込むドキュメントを切り替えます。

例:

```yaml
---
cue_card:
    urls:
        - 'https://example.com/cue-card-a-1'
        - 'https://example.com/cue-card-a-2'
--- # コメント
cue_card:
    urls:
        - 'https://example.com/cue-card-b-1'
        - 'https://example.com/cue-card-b-2'
---
cue_card:
    urls:
        - 'https://example.com/cue-card-c-1'
```

#### `--esperecyan-document-index=0` の場合
指定しなかった場合と同じ。

```json
{
	"cue_card": {
		"urls": [
			"https://example.com/cue-card-a-1",
			"https://example.com/cue-card-a-1"
		]
	}
}
```

#### `--esperecyan-document-index=1` の場合

```json
{
	"cue_card": {
		"urls": [
			"https://example.com/cue-card-b-1",
			"https://example.com/cue-card-b-1"
		]
	}
}
```

その他の機能
------------
### ニコニコ動画マイリストの展開
`import.video_playlist_uris` にニコニコ動画の公開マイリストのURLが含まれている場合、マイリストに含まれる動画のURLを取得して `import.video_content_uris` へ追加します。

```yaml
import:
    video_content_uris:
        - https://www.nicovideo.jp/watch/sm15633620
        - https://www.youtube.com/watch?v=KGt5WvFeMkw
    video_playlist_uris:
        - https://www.youtube.com/watch?v=4OUyE9YPRyA
        - https://www.nicovideo.jp/user/89622028/mylist/70543272
```

```json
{
	"import": {
		"video_content_uris": [
			"https://www.nicovideo.jp/watch/sm15633620",
			"https://www.youtube.com/watch?v=KGt5WvFeMkw",
			"http://www.nicovideo.jp/watch/sm38277590?ref=rss_mylist_rss2",
			"http://www.nicovideo.jp/watch/sm38277453?ref=rss_mylist_rss2",
			"http://www.nicovideo.jp/watch/sm38277122?ref=rss_mylist_rss2",
			"http://www.nicovideo.jp/watch/sm38276808?ref=rss_mylist_rss2"
		],
		"video_playlist_uris": [
			"https://www.youtube.com/watch?v=4OUyE9YPRyA",
			"https://www.nicovideo.jp/user/89622028/mylist/70543272"
		]
	}
}
```

Contribution
------------
Pull Request、または Issue よりお願いいたします。

ライセンス
----------
当アドオンのライセンスは [Mozilla Public License Version 2.0] \(MPL-2.0) です。

JavaScriptオブジェクトとYAML文字列の相互変換に次のライブラリを埋め込んでいます。

- [js-yaml] — [MIT License]
- [es5-shim] — [MIT License]
- [JSON 3] — [MIT License]

[Mozilla Public License Version 2.0]: https://www.mozilla.org/MPL/2.0/
[js-yaml]: https://github.com/nodeca/js-yaml
[es5-shim]: https://github.com/es-shims/es5-shim
[JSON 3]: https://github.com/bestiejs/json3
[MIT License]: https://ja.osdn.net/projects/opensource/wiki/licenses/MIT_license
