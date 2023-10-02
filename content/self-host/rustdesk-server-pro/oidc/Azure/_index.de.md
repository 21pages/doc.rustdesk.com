---
title: Azure
weight: 16
---

## Konfiguration

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
2. Suchen und w�hlen Sie **Microsoft Entra ID**.
3. W�hlen Sie im linken Men� [**App registrations**](https://portal.azure.com/#view/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/~/RegisteredApps) und klicken Sie **New registration**.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/1-Azure-NewRegistration.png)
4. �ffnen Sie die RustDesk Pro-Konsole und klicken Sie auf der Seite **Einstellungen** auf das Modul **OIDC**. Kopieren Sie dann die **Callback-URL**. **Hinweis**: Die **Callback-URL** ist nicht editierbar, der Teil `Pfad` ist auf `api/oidc/callback` festgelegt und der Teil `Protokoll://Host:Port` ist der Ursprung der aktuellen Webseite. Wenn Sie sie �ber die Adresse `http://localhost:8000/<Pfad>` �ffnen, lautet die **Callback-URL** `http://localhost:8000/api/oidc/callback`. Wenn Sie sie �ber die Adresse `https://192.168.0.1:8000/<Pfad>` �ffnen, dann ist die **Callback-URL** `https://192.168.0.1:8000/api/oidc/callback`. Da Azure `https://` oder `http://localhost` verwenden muss, w�hlen Sie bitte die entsprechende Adresse, um Ihre RustDesk Pro-Konsole zu �ffnen.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/12-RustDesk-Callback.png)
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/2-Azure-Register-RecirectURIs-Restrictions.png)
5. Geben Sie den **Namen** ein, w�hlen Sie die **Unterst�tzten Kontotypen** aus und f�gen Sie die **Redirect URI** von RustDesk Pro ein.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/2-Azure-Register.png)
6. Klicken Sie in RustDesk Pro auf **Neuer Autorisierungsanbieter**.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/3-RustDesk-NewAuthProvider.png)
7. W�hlen Sie in Azure die Anwendung aus, die Sie verwenden m�chten, klicken Sie auf **�bersicht** und kopieren Sie die **Anwendungs-(Client-)ID**.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/4-Azure-ClientID.png)
8. F�gen Sie in RustDesk Pro die **Client-ID** ein.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/5-RustDesk-ClientID.png)
9. Erstellen Sie in Azures **Zertifikate und Geheimnisse** ein neues oder w�hlen Sie ein Client-Geheimnis aus, normalerweise ein neues.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/6-Azure-NewOrSelectClientSecret.png)
10. Kopieren Sie in Azure den Wert des Client-Geheimnisses. **Hinweis**: Dieser Wert ist nur sichtbar, wenn Sie sich zum ersten Mal registrieren. Nachdem Sie die Seite verlassen haben, ist er nicht mehr sichtbar. Bitte bewahren Sie diesen Wert gut auf.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/7-Azure-CopySecretValue.png)
11. F�gen Sie in RustDesk Pro den Wert f�r das Client-Geheimnis ein.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/8-RustDesk-FillClientSecret.png)
12. F�llen Sie in RustDesk Pro das Feld **Issuer** mit `https://login.microsoftonline.com/<Directory (tenant) ID>/v2.0` aus. Bitte ersetzen Sie `Directory (tenant) ID` durch Ihre **Directory (tenant) ID**. Die **Directory (tenant) ID** befindet sich im Fenster **�bersicht** der Azure-App.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/9-RustDesk-Issuer.png)
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/10-Azure-TenantID.png)
13. W�hlen Sie in Azure das Men� **Authentifizierung**. Richten Sie dann die Autorisierung ein, indem Sie **ID-Token (Implizite Genehmigung und hybride Flows)** w�hlen.
![](/docs/en/self-host/rustdesk-server-pro/oidc/Azure/images/11-Azure-Auth.png)

## Fehlersuche

## Referenzen

- [OpenID Connect-Anbieter einrichten mit Azure AD](https://learn.microsoft.com/de-de/power-pages/security/authentication/openid-settings)
- [OpenID Connect auf Microsoft Identity Platform](https://learn.microsoft.com/de-de/azure/active-directory/develop/v2-protocols-oidc)
