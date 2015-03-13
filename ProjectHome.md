### Overview ###

Simple Java Google Translate API to translate any text from one language to another.
Supporting the connection through a proxy server with or without authentication.

Supports translation using [Google Translate API v1](http://code.google.com/apis/language/translate/v1/getting_started.html) and [Google Translate API v2](http://code.google.com/apis/language/translate/v2/getting_started.html).

Google Translate is a tool that automatically translates text from one language to another language (e.g. French to English). You can use the Google Translate API to programmatically translate text in your webpages or apps.

To use [Google Translate API v2](http://code.google.com/apis/language/translate/v2/getting_started.html) you need acquire an API key. Visit the [APIs Console](https://code.google.com/apis/console). In the Services pane, activate the Google Translate API; if the Terms of Service appear, read and accept them.
Next, go to the [API Access](https://code.google.com/apis/console#access) pane. The API key is near the bottom of that pane, in the section titled "Simple API Access."

#### List of translatable languages ####

| Language | Code |  | Language | Code |
|:---------|:-----|:-|:---------|:-----|
| AFRIKAANS | af |  | ITALIAN | it |
| ALBANIAN | sq |  | JAPANESE | ja |
| ARABIC | ar |  | KOREAN | ko |
| BELARUSIAN | be |  | LATVIAN | lv |
| BULGARIAN | bg |  | LITHUANIAN | lt |
| CATALAN | ca |  | MACEDONIAN | mk |
| CHINESE | zh |  | MALAY | ms |
| CHINESE\_SIMPLIFIED | zh-CN |  | MALTESE | mt |
| CHINESE\_TRADITIONAL | zh-TW |  | NORWEGIAN | no |
| CROATIAN | hr |  | PERSIAN | fa |
| CZECH | cs |  | POLISH | pl |
| DANISH | da |  | PORTUGUESE | pt |
| DUTCH | nl |  | PORTUGUESE\_PORTUGAL | pt-PT |
| ENGLISH | en |  | ROMANIAN | ro |
| ESTONIAN | et |  | RUSSIAN | ru |
| FILIPINO | tl |  | SERBIAN | sr |
| FINNISH | fi |  | SLOVAK | sk |
| FRENCH | fr |  | SLOVENIAN | sl |
| GALICIAN | gl |  | SPANISH | es |
| GERMAN | de |  | SWAHILI | sw |
| GREEK | el |  | SWEDISH | sv |
| HAITIAN\_CREOLE | ht |  | TAGALOG | tl |
| HEBREW | iw |  | THAI | th |
| HINDI | hi |  | TURKISH | tr |
| HUNGARIAN | hu |  | UKRAINIAN | uk |
| ICELANDIC | is |  | VIETNAMESE | vi |
| INDONESIAN | id |  | WELSH | cy |
| IRISH | ga |  | YIDDISH | yi |

### Getting Started with SimpleGoogleTranslator ###

```
package com.demo;

import com.translator.google.core.ProxyWrapper;
import com.translator.google.core.Translation;
import com.translator.google.translator.OnlineGoogleTranslator;
import com.translator.google.translator.OnlineGoogleTranslator.Language;
import java.io.IOException;

public class GoogleTranslationExample
{
	public static void main(String[] args) throws IOException
	{
		// general constants
		final String SOURCE_TEXT = "Hello, world!";
		final Language SOURCE_LANGUAGE = Language.ENGLISH;
		final Language TARGET_LANGUAGE = Language.RUSSIAN;

		// specific setting only for Google Translate API v2
		final String API_KEY = "INSERT-YOUR-KEY";

		// specific settings only for connection through proxy
		final String PROXY_HOST = "192.168.0.1";
		final int PROXY_PORT = 3128;
		final String PROXY_USERNAME = "User";
		final String PROXY_PASSWORD = "Password";

		// ***********************
		// Google Translate API v1
		// ***********************
		// using Google Translate API v1 without proxy
		OnlineGoogleTranslator translator = OnlineGoogleTranslator.createInstance();
		Translation translation = translator.translate(SOURCE_TEXT, SOURCE_LANGUAGE, TARGET_LANGUAGE);

		System.out.printf("In %s text: %s\n", SOURCE_LANGUAGE, SOURCE_TEXT);
		System.out.printf("In %s text: %s\n", TARGET_LANGUAGE, translation.getTranslatedText());

		// using Google Translate API v1 with connection through proxy without authentication
		translator = OnlineGoogleTranslator.createInstance(new ProxyWrapper(PROXY_HOST, PROXY_PORT));
		translation = translator.translate(SOURCE_TEXT, SOURCE_LANGUAGE, TARGET_LANGUAGE);

		System.out.printf("In %s text: %s\n", SOURCE_LANGUAGE, SOURCE_TEXT);
		System.out.printf("In %s text: %s\n", TARGET_LANGUAGE, translation.getTranslatedText());

		// using Google Translate API v1 with connection through proxy with authentication
		translator = OnlineGoogleTranslator.createInstance(new ProxyWrapper(PROXY_HOST, PROXY_PORT, PROXY_USERNAME, PROXY_PASSWORD));
		translation = translator.translate(SOURCE_TEXT, SOURCE_LANGUAGE, TARGET_LANGUAGE);

		System.out.printf("In %s text: %s\n", SOURCE_LANGUAGE, SOURCE_TEXT);
		System.out.printf("In %s text: %s\n", TARGET_LANGUAGE, translation.getTranslatedText());

		// ***********************
		// Google Translate API v2
		// ***********************
		// using Google Translate API v2 without proxy
		translator = OnlineGoogleTranslator.createInstance(API_KEY);
		translation = translator.translate(SOURCE_TEXT, SOURCE_LANGUAGE, TARGET_LANGUAGE);

		System.out.printf("In %s text: %s\n", SOURCE_LANGUAGE, SOURCE_TEXT);
		System.out.printf("In %s text: %s\n", TARGET_LANGUAGE, translation.getTranslatedText());

		// using Google Translate API v2 with connection through proxy without authentication
		translator = OnlineGoogleTranslator.createInstance(new ProxyWrapper(PROXY_HOST, PROXY_PORT), API_KEY);
		translation = translator.translate(SOURCE_TEXT, SOURCE_LANGUAGE, TARGET_LANGUAGE);

		System.out.printf("In %s text: %s\n", SOURCE_LANGUAGE, SOURCE_TEXT);
		System.out.printf("In %s text: %s\n", TARGET_LANGUAGE, translation.getTranslatedText());

		// using Google Translate API v2 with connection through proxy with authentication
		translator = OnlineGoogleTranslator.createInstance(new ProxyWrapper(PROXY_HOST, PROXY_PORT, PROXY_USERNAME, PROXY_PASSWORD), API_KEY);
		translation = translator.translate(SOURCE_TEXT, SOURCE_LANGUAGE, TARGET_LANGUAGE);

		System.out.printf("In %s text: %s\n", SOURCE_LANGUAGE, SOURCE_TEXT);
		System.out.printf("In %s text: %s\n", TARGET_LANGUAGE, translation.getTranslatedText());
	}
}
```

### Troubleshooting ###

If you encounter problems:

  1. Check your connection to the Internet
  1. Check availability of the proxy server (if you only use it)
  1. Make sure your API key is valid (if you only use Google Translate API v2)