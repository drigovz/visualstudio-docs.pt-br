---
title: Como definir configurações de depuração e de versão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703655"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Como definir configurações de depuração e versão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os projetos do Visual Studio têm configurações separadas de versão e depuração para seu programa. Como os nomes sugerem, você cria a versão de depuração para depuração e a versão de lançamento para a distribuição de versão final.  
  
 A configuração de depuração do seu programa é compilada com informações de depuração simbólicas completas e sem otimização. A otimização complica a depuração, porque a relação entre o código fonte e as instruções geradas é mais complexa.  
  
 A configuração de versão do programa não contém informações de depuração simbólicas e é totalmente otimizada. Informações de depuração podem ser geradas em Arquivos PDB, dependendo das opções do compilador que são usadas. Criar arquivos PDB pode ser muito útil se você posteriormente precisa depurar a versão de lançamento.  
  
 Para obter mais informações sobre configurações de compilação, consulte [noções básicas sobre configurações de compilação](../ide/understanding-build-configurations.md).  
  
 Você pode alterar a configuração de Build no menu **Compilar** , na barra de ferramentas ou nas páginas de propriedades do projeto. As páginas de propriedades do projeto são específicas do idioma. O procedimento a seguir mostra como alterar a configuração de Build no menu e na barra de ferramentas. Para obter mais informações sobre como alterar a configuração de compilação em projetos em idiomas diferentes, consulte a seção Tópicos relacionados abaixo.  
  
### <a name="to-change-the-build-configuration"></a>Para alterar a configuração da compilação  
  
1. No menu Compilar: clique em **Compilar/Configuration Manager**e, em seguida, selecione **depurar** ou **liberar**.  
  
2. Na barra de ferramentas, escolha **depurar** ou **liberar** na caixa de listagem **configurações da solução** .  
  
     ![configuração de Build da barra de ferramentas](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Essa barra de ferramentas não está disponível nas Express Editions. Você pode usar os itens de menu **criar solução F6** e **Iniciar depuração F5** para escolher a configuração.  
  
## <a name="see-also"></a>Consulte Também  
 [Configurações e preparação do depurador](../debugger/debugger-settings-and-preparation.md)   
 [Configurações do projeto para uma configuração de depuração do C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Configurações de projeto para configurações de depuração em C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Configurações de projeto para uma configuração de depuração de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Como: criar e editar configurações](../ide/how-to-create-and-edit-configurations.md)   
 [Debug and Release Project Configurations](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e) (Configurações de projeto de depuração e lançamento)
