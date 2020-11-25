---
title: Página de propriedades do aplicativo para aplicativos UWP
description: Saiba como usar a página de aplicativo para especificar o assembly do Plataforma Universal do Windows (UWP) e as informações do pacote e a versão de destino do Windows 10.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: reference
f1_keywords:
- AppPackage.Properties.Application
helpviewer_keywords:
- Application page [UWP project]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 826d408d8e1a6a2cb8bcad956ce930781a9155db
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871360"
---
# <a name="application-property-page-uwp-projects"></a>Página de propriedades do aplicativo (projetos UWP)

Use a página de projetos do **Aplicativo** para especificar informações de assembly e pacote do projeto UWP (Plataforma Universal do Windows) e a versão de destino do Windows 10.

![Página de propriedades do aplicativo](media/application-page-uwp.png)

Para acessar a página **Aplicativo**, escolha um nó do projeto **Gerenciador de Soluções**. Em seguida, escolha Propriedades do **projeto**  >  **Properties** na barra de menus. As páginas de propriedades são abertas na guia **Aplicativo**.

## <a name="general-section"></a>Seção geral

**Nome** &mdash; do assembly Especifica o nome do arquivo de saída que irá conter o manifesto do assembly.

Para acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.AssemblyName%2A>.

**Namespace padrão** &mdash; Especifica o namespace de base para arquivos adicionados ao projeto. Para saber mais sobre namespaces, confira [Namespaces (guia programação em C#)](/dotnet/csharp/programming-guide/namespaces/), [Namespaces (Visual Basic)](/dotnet/visual-basic/programming-guide/program-structure/namespaces) ou [Namespaces (C++)](/cpp/cpp/namespaces-cpp).

Para acessar essa propriedade de forma programática, consulte <xref:VSLangProj.ProjectProperties.RootNamespace%2A>.

**Informações** &mdash; do assembly A escolha desse botão exibe a [caixa de diálogo informações do assembly](../../ide/reference/assembly-information-dialog-box.md).

**Manifesto** &mdash; do pacote A escolha desse botão abre o designer de manifesto. O designer de manifesto também pode ser acessado escolhendo o arquivo _Package.appxmanifest_ no **Gerenciador de Soluções**. Para saber mais, confira [Configurar um pacote com o designer de manifesto](/windows/msix/package/packaging-uwp-apps#configure-your-project).

## <a name="targeting-section"></a>Seção de direcionamento

Você pode definir a versão de destino e a versão mínima do Windows 10 para seu aplicativo usando as listas suspensas nesta seção. Recomendamos que você direcione para a versão mais recente do Windows 10, e se você estiver desenvolvendo um aplicativo empresarial, que também ofereça suporte a uma versão mínima mais antiga. Para saber mais sobre qual versão do Windows 10 escolher, confira [Escolher uma versão do UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version).

Para obter informações sobre o direcionamento de plataforma no Visual Studio, confira [Direcionamento de plataforma](/visualstudio/productinfo/vs2017-compatibility-vs#platform-targeting).

## <a name="see-also"></a>Confira também

- [Criar seu primeiro aplicativo UWP](/windows/uwp/get-started/your-first-app)
- [Escolher uma versão do UWP](/windows/uwp/updates-and-versions/choose-a-uwp-version)
