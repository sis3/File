https://drive.google.com/file/d/1OnTCM0tgtnrO8AKtgE0EUCayikKrksI_/view?usp=drive_link


<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <!-- Supprimer le trailing slash -->
                <rule name="Remove trailing slash" stopProcessing="true">
                    <match url="(.*)/$" />
                    <conditions>
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                    </conditions>
                    <action type="Redirect" redirectType="Permanent" url="{R:1}" />
                </rule>

                <!-- Rediriger vers public si accès à la racine -->
                <rule name="Redirect to public" stopProcessing="true">
                    <match url="^(.*)$" />
                    <conditions logicalGrouping="MatchAll" trackAllCaptures="false">
                        <add input="{REQUEST_URI}" pattern="^/public/" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Redirect" url="/public/{R:1}" />
                </rule>

                <!-- Règles pour Laravel -->
                <rule name="Laravel Front Controller" stopProcessing="true">
                    <match url="^(.*)$" ignoreCase="false" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="index.php" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>

    <!-- Configuration pour PWA -->
    <system.webServer>
        <staticContent>
            <mimeMap fileExtension=".json" mimeType="application/json" />
            <mimeMap fileExtension=".webmanifest" mimeType="application/manifest+json" />
        </staticContent>
    </system.webServer>
</configuration>
