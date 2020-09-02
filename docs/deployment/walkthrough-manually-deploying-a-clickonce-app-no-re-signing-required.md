---
title: Implantar manualmente os aplicativos ClickOnce que preservam a identidade visual
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- branding
- preserved branding information
- ClickOnce deployment, manually
- multiple ClickOnce deployment and branding
- ClickOnce deployment, SDK tools
- customer deployments
- manual ClickOnce deployments
- manifests [ClickOnce]
- ClickOnce applications, deployed by others
ms.assetid: c21822fb-d4ee-42e4-b72d-41ee9786efe5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 47db202d07fd88bfb5e922964caf2cdd5008c6fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66263420"
---
# <a name="walkthrough-manually-deploy-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information"></a>Walkthrough: implantar manualmente um aplicativo ClickOnce que não requer nova assinatura e que preserva informações de identidade visual
Ao criar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo e, em seguida, fornecê-lo a um cliente para publicar e implantar, o cliente tradicionalmente teve de atualizar o manifesto de implantação e assinar novamente. Embora esse ainda seja o método preferencial na maioria dos casos, o .NET Framework 3,5 permite que você crie implantações [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] que podem ser implantadas pelos clientes sem a necessidade de regenerar um novo manifesto de implantação. Para obter mais informações, consulte [implantar aplicativos ClickOnce para servidores de teste e produção sem assinatura](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md).

 Quando você cria um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo e o fornece a um cliente para publicar e implantar, o aplicativo pode usar a identidade visual do cliente ou pode preservar sua identidade visual. Por exemplo, se o aplicativo for um aplicativo proprietário único, talvez você queira preservar sua identidade visual. Se o aplicativo for altamente personalizado para cada cliente, talvez você queira usar a identidade visual do cliente. O .NET Framework 3,5 permite preservar sua identidade visual, informações do Publicador e assinatura de segurança quando você dá a um aplicativo a uma organização para implantação. Para obter mais informações, consulte [criar aplicativos ClickOnce para outras pessoas a serem implantadas](../deployment/creating-clickonce-applications-for-others-to-deploy.md).

> [!NOTE]
> Neste tutorial, você cria implantações manualmente usando a ferramenta de linha de comando *Mage.exe* ou a ferramenta gráfica *MageUI.exe*. Para obter mais informações sobre implantações manuais, consulte [Walkthrough: implantar manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

## <a name="prerequisites"></a>Pré-requisitos
 Para executar as etapas neste passo a passos, você precisará do seguinte:

- Um aplicativo Windows Forms que você está pronto para implantar. Esse aplicativo será chamado de *WindowsFormsApp1*.

- Visual Studio ou o SDK do Windows.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageexe"></a>Para implantar um aplicativo ClickOnce com várias implantações e suporte de identidade visual usando o Mage.exe

1. Abra um prompt de comando do Visual Studio ou um [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt de comando e altere para o diretório no qual você armazenará seus [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos.

2. Crie um diretório chamado após a versão atual da sua implantação. Se esta for a primeira vez que você está implantando o aplicativo, você provavelmente escolherá **1.0.0.0**.

   > [!NOTE]
   > A versão da sua implantação pode ser distinta da versão dos arquivos do aplicativo.

3. Crie um subdiretório chamado **bin** e copie todos os seus arquivos de aplicativo aqui, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados.

4. Gere o manifesto do aplicativo com uma chamada para Mage.exe.

   ```cmd
   mage -New Application -ToFile 1.0.0.0\WindowsFormsApp1.exe.manifest -Name "Windows Forms App 1" -Version 1.0.0.0 -FromDirectory 1.0.0.0\bin -UseManifestForTrust true -Publisher "A. Datum Corporation"
   ```

5. Assine o manifesto do aplicativo com seu certificado digital.

   ```cmd
   mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx
   ```

6. Gere o manifesto de implantação com uma chamada para *Mage.exe*. Por padrão, *Mage.exe* marcará sua [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação como um aplicativo instalado, para que possa ser executada online e offline. Para disponibilizar o aplicativo somente quando o usuário estiver online, use o `-i` argumento com um valor de `f` . Como esse aplicativo aproveitará o recurso de implantação múltipla, exclua o `-providerUrl` argumento para *Mage.exe*. (Em versões do .NET Framework antes da versão 3,5, a exclusão `-providerUrl` de um aplicativo offline resultará em um erro.)

   ```cmd
   mage -New Deployment -ToFile WindowsFormsApp1.application -Name "Windows Forms App 1" -Version 1.0.0.0 -AppManifest 1.0.0.0\WindowsFormsApp1.manifest
   ```

7. Não assine o manifesto de implantação.

8. Forneça todos os arquivos para o cliente, que implantará o aplicativo em sua rede.

9. Neste ponto, o cliente deve assinar o manifesto de implantação com seu próprio certificado gerado automaticamente. Por exemplo, se o cliente trabalha para uma empresa chamada Adventure Works, ele pode gerar um certificado autoassinado usando a ferramenta de *MakeCert.exe* . Em seguida, use a ferramenta *Pvk2pfx.exe* para combinar os arquivos criados por *MakeCert.exe* em um arquivo PFX que pode ser passado para *Mage.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

10. O cliente seguinte usa esse certificado para assinar o manifesto de implantação.

    ```cmd
    mage -Sign WindowsFormsApp1.application -CertFile MyCert.pfx
    ```

11. O cliente implanta o aplicativo para seus usuários.

### <a name="to-deploy-a-clickonce-application-with-multiple-deployment-and-branding-support-using-mageuiexe"></a>Para implantar um aplicativo ClickOnce com várias implantações e suporte de identidade visual usando o MageUI.exe

1. Abra um prompt de comando do Visual Studio ou um [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] prompt de comando e navegue até o diretório no qual você armazenará seus [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] arquivos.

2. Crie um subdiretório chamado **bin** e copie todos os seus arquivos de aplicativo aqui, incluindo arquivos executáveis, assemblies, recursos e arquivos de dados.

3. Crie um subdiretório chamado após a versão atual da sua implantação. Se esta for a primeira vez que você está implantando o aplicativo, você provavelmente escolherá **1.0.0.0**.

   > [!NOTE]
   > A versão da sua implantação pode ser distinta da versão dos arquivos do aplicativo.

4. Mova o \\ diretório **bin** para o diretório que você criou na etapa 2.

5. Inicie a ferramenta gráfica *MageUI.exe*.

   ```cmd
   MageUI.exe
   ```

6. Crie um novo manifesto de aplicativo selecionando **arquivo**, **novo**, **manifesto do aplicativo** no menu.

7. Na guia **nome** padrão, insira o nome e o número de versão dessa implantação. Além disso, forneça um valor para o **Editor**, que será usado como o nome da pasta para o link de atalho do aplicativo no menu iniciar quando ele for implantado.

8. Selecione a guia **Opções do aplicativo** e clique em usar o **manifesto do aplicativo para obter informações de confiança**. Isso habilitará a identidade visual de terceiros para esse [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.

9. Selecione a guia **arquivos** e clique no botão **procurar** ao lado da caixa de texto **diretório de aplicativo** .

10. Selecione o diretório que contém os arquivos de aplicativo que você criou na etapa 2 e clique em **OK** na caixa de diálogo seleção de pasta.

11. Clique no botão **popular** para adicionar todos os seus arquivos de aplicativo à lista de arquivos. Se seu aplicativo contiver mais de um arquivo executável, marque o arquivo executável principal para essa implantação como o aplicativo de inicialização selecionando **ponto de entrada** na lista suspensa **tipo de arquivo** . (Se seu aplicativo contiver apenas um arquivo executável, *MageUI.exe* irá marcá-lo para você.)

12. Selecione a guia **permissões necessárias** e selecione o nível de confiança que você precisa que seu aplicativo declare. O padrão é **confiança total**, que será apropriado para a maioria dos aplicativos.

13. Selecione **arquivo**, **salvar** no menu e salve o manifesto do aplicativo. Você será solicitado a assinar o manifesto do aplicativo quando salvá-lo.

14. Se você tiver um certificado armazenado como um arquivo no sistema de arquivos, use a opção **assinar como arquivo de certificado** e selecione o certificado do sistema de arquivos usando o botão de reticências (**...**).

     - ou -

     Se o certificado for mantido em um repositório de certificados que pode ser acessado do seu computador, selecione a **opção assinar com o certificado armazenado**e selecione o certificado na lista fornecida.

15. Selecione **arquivo**, **novo**, **manifesto de implantação** no menu para criar seu manifesto de implantação e, na guia **nome** , forneça um nome e um número de versão (**1.0.0.0** neste exemplo).

16. Alterne para a guia **Atualizar** e especifique com que frequência você deseja que esse aplicativo seja atualizado. Se seu aplicativo usar a [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] API de implantação para verificar se há atualizações em si, desmarque a caixa de seleção denominada **este aplicativo deve verificar se há atualizações**.

17. Alterne para a guia **referência de aplicativo** . Você pode preencher previamente todos os valores nessa guia clicando no botão **selecionar manifesto** e selecionando o manifesto do aplicativo criado nas etapas anteriores.

18. Escolha **salvar** e salve o manifesto de implantação no disco. Você será solicitado a assinar o manifesto do aplicativo quando salvá-lo. Clique em **Cancelar** para salvar o manifesto sem assiná-lo.

19. Forneça todos os arquivos de aplicativo para o cliente.

20. Neste ponto, o cliente deve assinar o manifesto de implantação com seu próprio certificado gerado automaticamente. Por exemplo, se o cliente trabalha para uma empresa chamada Adventure Works, ele pode gerar um certificado autoassinado usando a ferramenta de *MakeCert.exe* . Em seguida, use a ferramenta *Pvk2pfx.exe* para combinar os arquivos criados por *MakeCert.exe* em um arquivo PFX que pode ser passado para *MageUI.exe*.

    ```cmd
    makecert -r -pe -n "CN=Adventure Works" -sv MyCert.pvk MyCert.cer
    pvk2pfx.exe -pvk MyCert.pvk -spc MyCert.cer -pfx MyCert.pfx
    ```

21. Com o certificado gerado, o cliente agora assina o manifesto de implantação abrindo o manifesto de implantação no *MageUI.exe*e, em seguida, salvando-o. Quando a caixa de diálogo assinatura for exibida, o cliente selecionará a opção **assinar como arquivo de certificado** e escolherá o arquivo PFX salvo no disco.

22. O cliente implanta o aplicativo para seus usuários.

## <a name="see-also"></a>Confira também
- [Mage.exe (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [MageUI.exe (Manifest Generation and Editing Tool, cliente gráfico)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
- [MakeCert](/windows/desktop/SecCrypto/makecert)
