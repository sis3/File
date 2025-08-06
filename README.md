https://drive.google.com/file/d/1OnTCM0tgtnrO8AKtgE0EUCayikKrksI_/view?usp=drive_link


<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <!-- 1. Redirection invisible depuis la racine vers /public/ -->
                <rule name="HiddenRedirectToPublic" stopProcessing="true">
                    <match url="^(.*)$" />
                    <conditions logicalGrouping="MatchAll" trackAllCaptures="false">
                        <add input="{REQUEST_URI}" pattern="^/public/" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="/public/{R:1}" />
                </rule>

                <!-- 2. Gestion des routes Laravel dans public/ -->
                <rule name="LaravelFrontController" stopProcessing="true">
                    <match url="^(.*)$" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="/public/index.php/{R:1}" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>











<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="Redirect to public" stopProcessing="true">
                    <match url="(.*)" />
                    <conditions logicalGrouping="MatchAll" trackAllCaptures="false">
                        <add input="{REQUEST_URI}" pattern="^/public/" negate="true" />
                    </conditions>
                    <action type="Redirect" url="/public/{R:1}" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
