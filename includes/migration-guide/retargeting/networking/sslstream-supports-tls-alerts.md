### <a name="sslstream-supports-tls-alerts"></a>SslStream поддерживает TLS оповещения

|   |   |
|---|---|
|Подробные сведения|После сбоя подтверждения TLS при первой операции ввода-вывода чтения и записи возникнет <xref:System.IO.IOException?displayProperty=name> с внутренним исключением <xref:System.ComponentModel.Win32Exception?displayProperty=name>. Код <xref:System.ComponentModel.Win32Exception.NativeErrorCode?displayProperty=name> для <xref:System.ComponentModel.Win32Exception?displayProperty=name> можно сопоставить с TLS-предупреждением от удаленной стороны с помощью этой [документации по Schannel](https://msdn.microsoft.com/library/windows/desktop/dd721886%28v=vs.85%29.aspx). Дополнительные сведения см. в [RFC 2246. Раздел 7.2.2. Оповещение об ошибке](https://tools.ietf.org/html/rfc2246#section-7.2.2)В .NET 4.6.2 и более ранних версиях канал транспорта (как правило, TCP-соединение) будет ожидать во время операции записи или чтения, если другая сторона не предоставила подтверждение и сразу после этого отклонила соединение.|
|Предложение|Приложения, вызывающие сетевые API-интерфейсы ввода-вывода, например <xref:System.IO.Stream.Read(System.Byte[],System.Int32,System.Int32)>/<xref:System.IO.Stream.Write(System.Byte[],System.Int32,System.Int32)>, должны обрабатывать <xref:System.IO.IOException> или <xref:System.TimeoutException?displayProperty=name>. Начиная с версии .NET 4.7 функция оповещений TLS включена по умолчанию. В приложениях, предназначенных для версий с .NET 4.0 по .NET 4.6.2 и выполняемых на платформе .NET 4.7 или более поздней версии, эта функция будет отключена для сохранения совместимости. Чтобы включить или отключить эту функцию для приложений, предназначенных для .NET 4.6 и более поздних версий и выполняющихся на версии платформы .NET 4.7 или более поздней, доступна следующая конфигурация API.<ul><li>Программное выполнение:</li></ul>Это должно быть первым, что делает приложение, поскольку ServicePointManager будет инициализироваться только один раз:<pre><code class="language-C#">AppContext.SetSwitch(&quot;TestSwitch.LocalAppContext.DisableCaching&quot;, true);&#13;&#10;AppContext.SetSwitch(&quot;Switch.System.Net.DontEnableTlsAlerts&quot;, true); // Set to &#39;false&#39; to enable the feature in .NET 4.6 - 4.6.2.&#13;&#10;</code></pre><ul><li>AppConfig:</li></ul><pre><code class="language-XML">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableTlsAlerts=true&quot;/&gt;&#13;&#10;&lt;!-- Set to &#39;false&#39; to enable the feature in .NET 4.6 - 4.6.2. --&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre><ul><li>Раздел реестра (глобальный):</li></ul>Установите значение false, чтобы включить эту функцию в .NET 4.6–4.6.2.<pre><code>Key = HKLM\SOFTWARE\[Wow6432Node\]Microsoft\.NETFramework\AppContext\Switch.System.Net.DontEnableTlsAlerts&#13;&#10;Type = String&#13;&#10;Value = &quot;true&quot;&#13;&#10;</code></pre>|
|Область|Пограничный случай|
|Версия|4.7|
|Тип|Изменение целевой платформы|
|Затронутые API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.WebRequest?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.Http?displayProperty=nameWithType></li></ul>|
