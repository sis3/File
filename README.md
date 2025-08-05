https://drive.google.com/file/d/1OnTCM0tgtnrO8AKtgE0EUCayikKrksI_/view?usp=drive_link


<configuration>
    <system.webServer>
        <rewrite>
            <rules>
                <!-- Redirige toutes les requêtes vers /public/index.php -->
                <rule name="Redirect to Public Index" stopProcessing="true">
                    <match url="^(.*)$" />
                    <conditions logicalGrouping="MatchAll">
                        <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                        <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                    </conditions>
                    <action type="Rewrite" url="/public/index.php" />
                </rule>
            </rules>
        </rewrite>
    </system.webServer>
</configuration>
