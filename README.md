https://drive.google.com/file/d/1OnTCM0tgtnrO8AKtgE0EUCayikKrksI_/view?usp=drive_link


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
