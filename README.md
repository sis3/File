https://drive.google.com/file/d/1OnTCM0tgtnrO8AKtgE0EUCayikKrksI_/view?usp=drive_link


<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <rule name="Rewrite to Public Index" stopProcessing="true">
                    <match url="^(.*)$" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="public/index.php" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
