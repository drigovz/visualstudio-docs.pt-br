---
title: 'Como: Configurar o clickOnce Trust Prompt Behavior | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- deploying applications [ClickOnce], trust prompt
- ClickOnce applications, install without prompting
- ClickOnce applications, trust prompt
- ClickOnce deployment, trust prompt
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec5f1cca49f1b799b39969849e0a73bf1e6e296d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649141"
---
# <a name="how-to-configure-the-clickonce-trust-prompt-behavior"></a>Como configurar o comportamento do prompt confiável do ClickOnce
Você pode configurar o prompt de confiança do ClickOnce para controlar se os usuários finais têm a opção de instalar aplicativos ClickOnce, como aplicativos do Windows Forms, aplicativos do Windows Presentation Foundation, aplicativos de console, aplicativos do navegador WPF e soluções do Office. Você configura o prompt de confiança definindo as chaves de registro no computador de cada usuário final.

 A tabela a seguir mostra as opções de configuração que podem ser aplicadas a cada uma das cinco regiões (Internet, UntrustedSites, MyComputer, LocalIntranet e TrustedSites).

|Opção|Valor de definição de registro|Descrição|
|------------|----------------------------|-----------------|
|Habilite o prompt de confiança.|`Enabled`|O prompt de confiança do ClickOnce é exibido para que os usuários finais possam conceder confiança aos aplicativos ClickOnce.|
|Restringir o aviso de confiança.|`AuthenticodeRequired`|O prompt de confiança ClickOnce só será exibido se os aplicativos ClickOnce forem assinados com um certificado que identifica o editor.|
|Desabilite o aviso de confiança.|`Disabled`|O prompt de confiança ClickOnce não é exibido para quaisquer aplicativos ClickOnce que não estejam assinados com um certificado explicitamente confiável.|

 A tabela a seguir mostra o comportamento padrão de cada região. A coluna Aplicativos refere-se aos aplicativos do Windows Forms, aplicativos do Windows Presentation Foundation, aplicativos do navegador WPF e aplicativos de console.

|Zona|Aplicativos|Soluções do Office|
|----------|------------------|----------------------|
|`MyComputer`|`Enabled`|`Enabled`|
|`LocalIntranet`|`Enabled`|`Enabled`|
|`TrustedSites`|`Enabled`|`Enabled`|
|`Internet`|`Enabled`|`AuthenticodeRequired`|
|`UntrustedSites`|`Disabled`|`Disabled`|

 Você pode substituir essas configurações ativando, restringindo ou desativando o prompt de confiança ClickOnce.

## <a name="enable-the-clickonce-trust-prompt"></a>Habilitar o prompt de confiança ClickOnce
 Habilite o prompt de confiança para uma região quando você quiser que os usuários finais sejam apresentados com a opção de instalar e executar qualquer aplicativo ClickOnce que venha dessa região.

#### <a name="to-enable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para ativar o prompt de confiança do ClickOnce usando o editor de registro

1. Abra o Editor do Registro:

    1. Clique em **Iniciar** e em **Executar**.

    2. Na **caixa Abrir,** digite `regedit`e clique em **OK**.

2. Encontre a seguinte chave de registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se a chave não existe, crie-a.

3. Adicione as seguintes subchaves como **Valor de seqüência,** se elas ainda não existirem, com os valores associados mostrados na tabela a seguir.

    |Subchave de valor de cadeia|Valor|
    |-------------------------|-----------|
    |`Internet`|`Enabled`|
    |`UntrustedSites`|`Disabled`|
    |`MyComputer`|`Enabled`|
    |`LocalIntranet`|`Enabled`|
    |`TrustedSites`|`Enabled`|

     Para soluções `Internet` office, `AuthenticodeRequired` tem `UntrustedSites` o `Disabled`valor padrão e tem o valor . Para todos `Internet` os outros, `Enabled`tem o valor padrão.

#### <a name="to-enable-the-clickonce-trust-prompt-programmatically"></a>Para ativar o prompt de confiança ClickOnce programáticamente

1. Crie um aplicativo de console Visual Basic ou Visual C# no Visual Studio.

2. Abra o *arquivo Program.vb* ou *Program.cs* para edição e adicione o seguinte código.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Enabled")
    key.SetValue("LocalIntranet", "Enabled")
    key.SetValue("Internet", "Enabled")
    key.SetValue("TrustedSites", "Enabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Enabled");
    key.SetValue("LocalIntranet", "Enabled");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "Enabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Criar e executar o aplicativo.

## <a name="restrict-the-clickonce-trust-prompt"></a>Restringir o prompt de confiança ClickOnce
 Restringir o prompt de confiança para que as soluções sejam assinadas com certificados Authenticode que tenham identidade conhecida antes que os usuários sejam solicitados a uma decisão de confiança.

#### <a name="to-restrict-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para restringir o prompt de confiança do ClickOnce usando o editor de registro

1. Abra o Editor do Registro:

    1. Clique em **Iniciar** e em **Executar**.

    2. Na **caixa Abrir,** digite `regedit`e clique em **OK**.

2. Encontre a seguinte chave de registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se a chave não existe, crie-a.

3. Adicione as seguintes subchaves como **Valor de seqüência,** se elas ainda não existirem, com os valores associados mostrados na tabela a seguir.

    |Subchave de valor de cadeia|Valor|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`AuthenticodeRequired`|
    |`MyComputer`|`AuthenticodeRequired`|
    |`LocalIntranet`|`AuthenticodeRequired`|
    |`TrustedSites`|`AuthenticodeRequired`|

#### <a name="to-restrict-the-clickonce-trust-prompt-programmatically"></a>Para restringir o prompt de confiança ClickOnce programáticamente

1. Crie um aplicativo de console Visual Basic ou Visual C# no Visual Studio.

2. Abra o *arquivo Program.vb* ou *Program.cs* para edição e adicione o seguinte código.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "AuthenticodeRequired")
    key.SetValue("LocalIntranet", "AuthenticodeRequired")
    key.SetValue("Internet", "AuthenticodeRequired")
    key.SetValue("TrustedSites", "AuthenticodeRequired")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "AuthenticodeRequired");
    key.SetValue("LocalIntranet", "AuthenticodeRequired");
    key.SetValue("Internet", "AuthenticodeRequired");
    key.SetValue("TrustedSites", "AuthenticodeRequired");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();
    ```

3. Criar e executar o aplicativo.

## <a name="disable-the-clickonce-trust-prompt"></a>Desativar o prompt de confiança ClickOnce
 Você pode desativar o prompt de confiança para que os usuários finais não sejam dadas a opção de instalar soluções que ainda não são confiáveis em sua política de segurança.

#### <a name="to-disable-the-clickonce-trust-prompt-by-using-the-registry-editor"></a>Para desativar o prompt de confiança do ClickOnce usando o editor de registro

1. Abra o Editor do Registro:

    1. Clique em **Iniciar** e em **Executar**.

    2. Na **caixa Abrir,** digite `regedit`e clique em **OK**.

2. Encontre a seguinte chave de registro:

     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\.NETFramework\Security\TrustManager\PromptingLevel**

     Se a chave não existe, crie-a.

3. Adicione as seguintes subchaves como **Valor de seqüência,** se elas ainda não existirem, com os valores associados mostrados na tabela a seguir.

    |Subchave de valor de cadeia|Valor|
    |-------------------------|-----------|
    |`UntrustedSites`|`Disabled`|
    |`Internet`|`Disabled`|
    |`MyComputer`|`Disabled`|
    |`LocalIntranet`|`Disabled`|
    |`TrustedSites`|`Disabled`|

#### <a name="to-disable-the-clickonce-trust-prompt-programmatically"></a>Para desativar o prompt de confiança clickOnce programáticamente

1. Crie um aplicativo de console Visual Basic ou Visual C# no Visual Studio.

2. Abra o *arquivo Program.vb* ou *Program.cs* para edição e adicione o seguinte código.

    ```vb
    Dim key As Microsoft.Win32.RegistryKey
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")
    key.SetValue("MyComputer", "Disabled")
    key.SetValue("LocalIntranet", "Disabled")
    key.SetValue("Internet", "Disabled")
    key.SetValue("TrustedSites", "Disabled")
    key.SetValue("UntrustedSites", "Disabled")
    key.Close()
    ```

    ```csharp
    Microsoft.Win32.RegistryKey key;
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");
    key.SetValue("MyComputer", "Disabled");
    key.SetValue("LocalIntranet", "Disabled");
    key.SetValue("Internet", "Disabled");
    key.SetValue("TrustedSites", "Disabled");
    key.SetValue("UntrustedSites", "Disabled");
    key.Close();

    ```

3. Criar e executar o aplicativo.

## <a name="see-also"></a>Confira também
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)
- [Visão geral da implantação de aplicativos confiáveis](../deployment/trusted-application-deployment-overview.md)
- [Como habilitar as configurações de segurança do ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Como definir uma zona de segurança em um aplicativo ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Como definir permissões personalizadas em um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Como depurar um aplicativo ClickOnce com permissões restritas](securing-clickonce-applications.md)
- [Como adicionar um fornecedor confiável a um computador cliente em aplicativos ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Como reassinar manifestos do aplicativo e de implantação](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
