---
title: Criar um instalador personalizado para o aplicativo ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b648134b7ad27a8f622ce270dc0f05e0a7e6516c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637416"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Walkthrough: criar um instalador personalizado para um aplicativo ClickOnce
Qualquer aplicativo ClickOnce baseado em um arquivo *. exe* pode ser instalado e atualizado silenciosamente por um instalador personalizado. Um instalador personalizado pode implementar a experiência do usuário personalizada durante a instalação, incluindo caixas de diálogo personalizadas para operações de segurança e manutenção. Para executar operações de instalação, o instalador personalizado usa a classe <xref:System.Deployment.Application.InPlaceHostingManager>. Este tutorial demonstra como criar um instalador personalizado que instala silenciosamente um aplicativo ClickOnce.

## <a name="prerequisites"></a>Prerequisites

### <a name="to-create-a-custom-clickonce-application-installer"></a>Para criar um instalador de aplicativo ClickOnce personalizado

1. Em seu aplicativo ClickOnce, adicione referências a System. Deployment e System. Windows. Forms.

2. Adicione uma nova classe ao seu aplicativo e especifique qualquer nome. Este tutorial usa o nome `MyInstaller`.

3. Adicione as seguintes `Imports` ou `using` diretivas à parte superior da sua nova classe.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Adicione os métodos a seguir à sua classe.

     Esses métodos chamam <xref:System.Deployment.Application.InPlaceHostingManager> métodos para baixar o manifesto de implantação, declarar as permissões apropriadas, solicitar permissão ao usuário para instalar e, em seguida, baixar e instalar o aplicativo no cache do ClickOnce. Um instalador personalizado pode especificar que um aplicativo ClickOnce é previamente confiável ou pode adiar a decisão de confiança para a chamada do método <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>. Esse código pré-confia no aplicativo.

    > [!NOTE]
    > As permissões atribuídas pela pré-confiança não podem exceder as permissões do código do instalador personalizado.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Para tentar a instalação do seu código, chame o método `InstallApplication`. Por exemplo, se você tiver nomeado sua classe `MyInstaller`, poderá chamar `InstallApplication` da seguinte maneira.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Próximas etapas
 Um aplicativo ClickOnce também pode adicionar lógica de atualização personalizada, incluindo uma interface do usuário personalizada para mostrar durante o processo de atualização. Para obter mais informações, consulte <xref:System.Deployment.Application.UpdateCheckInfo>. Um aplicativo ClickOnce também pode suprimir a entrada do menu Iniciar padrão, atalho e adicionar ou remover programas usando um elemento `<customUX>`. Para obter mais informações, consulte [\<entryPoint elemento >](../deployment/entrypoint-element-clickonce-application.md) e <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>Consulte também
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
- [Elemento \<entryPoint>](../deployment/entrypoint-element-clickonce-application.md)
