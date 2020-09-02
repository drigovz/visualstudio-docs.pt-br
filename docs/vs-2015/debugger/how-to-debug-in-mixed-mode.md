---
title: 'Como: Depurar no modo misto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e2dd4ea0000eefdbd9f74c8fa97c4c63e06fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681141"
---
# <a name="how-to-debug-in-mixed-mode"></a>Como depurar no modo misto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os procedimentos a seguir descrevem como depurar código gerenciado e código nativo, também conhecido depuração de modo misto. Há dois cenários para fazer isso, dependendo de a DLL ou o aplicativo serem escritos em código nativo:  
  
- O aplicativo de chamada que chama a DLL é escrito em código nativo. Nesse caso, a DLL é gerenciada e os depuradores gerenciados e nativos devem estar habilitados para depurar ambos. Você pode verificar isso na caixa de diálogo ** \<Project> páginas de propriedades** . Como você faz isso depende de a depuração ser iniciada do projeto de DLL ou do projeto de aplicativo de chamada.  
  
- O aplicativo de chamada que chama a DLL é escrito em código gerenciado e sua DLL é escrita em código nativo.  
  
> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Para habilitar a depuração de modo misto  
  
1. Em **Gerenciador de soluções**, selecione o projeto.  
  
2. No menu **Exibir**, clique em **Página de Propriedades**.  
  
3. Na caixa de diálogo ** \<Project> páginas de propriedades** , expanda o nó **Propriedades de configuração** e, em seguida, selecione **depuração**.  
  
4. Defina **Tipo de Depurador** como **Misto** ou **Automático**.  
  
## <a name="see-also"></a>Consulte Também  
 [Como: Depurar de um projeto de DLL](../debugger/how-to-debug-from-a-dll-project.md)
