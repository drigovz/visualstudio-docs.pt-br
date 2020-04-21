---
title: 'Como: Re-assinar Manifestos de Aplicação e Implantação | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649178"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Como assinar manifestos de aplicativo e implantação novamente
Depois de fazer alterações nas propriedades de implantação no manifesto de aplicativos do Windows Forms, aplicativos do Windows Presentation Foundation (xbap) ou soluções do Office, você deve reassinar os manifestos de aplicativo e implantação com um certificado. Esse processo ajuda a garantir que arquivos violados não sejam instalados nos computadores dos usuários finais.

 Outro cenário em que você pode reassinar os manifestos é quando seus clientes querem assinar o aplicativo e a implantação se manifesta com seu próprio certificado.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Assinar novamente os manifestos de aplicativo e de implantação
 Este procedimento pressupõe que você já tenha feito alterações no seu arquivo manifesto de solicitação *(.manifest*). Para obter mais informações, consulte [Como: Alterar propriedades de implantação](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para reassinar o aplicativo e a implantação se manifesta com o Mage.exe

1. Abra uma janela **prompt de comando do Visual Studio.**

2. Alterar diretórios para a pasta que contém os arquivos manifestos que você deseja assinar.

3. Digite o seguinte comando para assinar o arquivo manifesto do aplicativo. Substitua *ManifestFileName* pelo nome do seu arquivo manifesto mais a extensão. Substitua o *Certificado* pelo caminho relativo ou totalmente qualificado do arquivo do certificado e *substitua a senha* pelo certificado.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Por exemplo, você pode executar o seguinte comando para assinar um manifesto de aplicativo para um complemento, um aplicativo do Formulário Windows ou um aplicativo de navegador da Windows Presentation Foundation. Certificados temporários criados pelo Visual Studio não são recomendados para implantação em ambientes de produção.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Digite o seguinte comando para atualizar e assinar o arquivo manifesto de implantação, substituindo os nomes do espaço reservado como na etapa anterior.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Por exemplo, você pode executar o seguinte comando para atualizar e assinar um manifesto de implantação para um complemento do Excel, um aplicativo do Windows Forms ou um aplicativo de navegador da Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Opcionalmente, copie o manifesto de implantação mestre*\\\<(publique o nome do aplicativo>.application)* para o diretório de implantação da sua versão *(publique\Arquivos\\\<de aplicativos nome\<>_ versão>*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Atualizar e reassinar os manifestos de aplicação e implantação
 Este procedimento pressupõe que você já tenha feito alterações no seu arquivo manifesto de solicitação *(.manifest),* mas que existem outros arquivos que foram atualizados. Quando os arquivos são atualizados, o hash que representa o arquivo também deve ser atualizado.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Para atualizar e reassinar o aplicativo e a implantação se manifesta com o Mage.exe

1. Abra uma janela **prompt de comando do Visual Studio.**

2. Alterar diretórios para a pasta que contém os arquivos manifestos que você deseja assinar.

3. Remova a extensão de arquivo *.deploy* dos arquivos na pasta de saída de publicação.

4. Digite o seguinte comando para atualizar o manifesto do aplicativo com os novos hashes para os arquivos atualizados e assinar o arquivo manifesto do aplicativo. Substitua *ManifestFileName* pelo nome do seu arquivo manifesto mais a extensão. Substitua o *Certificado* pelo caminho relativo ou totalmente qualificado do arquivo do certificado e *substitua a senha* pelo certificado.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Por exemplo, você pode executar o seguinte comando para assinar um manifesto de aplicativo para um complemento, um aplicativo do Formulário Windows ou um aplicativo de navegador da Windows Presentation Foundation. Certificados temporários criados pelo Visual Studio não são recomendados para implantação em ambientes de produção.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Digite o seguinte comando para atualizar e assinar o arquivo manifesto de implantação, substituindo os nomes do espaço reservado como na etapa anterior.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Por exemplo, você pode executar o seguinte comando para atualizar e assinar um manifesto de implantação para um complemento do Excel, um aplicativo do Windows Forms ou um aplicativo de navegador da Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Adicione a extensão de arquivo *.deploy* de volta aos arquivos, exceto os arquivos manifestos de aplicação e implantação.

7. Opcionalmente, copie o manifesto de implantação mestre*\\\<(publique o nome do aplicativo>.application)* para o diretório de implantação da sua versão *(publique\Arquivos\\\<de aplicativos nome\<>_ versão>*).

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
- [Como configurar o comportamento do prompt confiável do ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)