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
ms.openlocfilehash: 9939c3eef0c2037e02c23573e246dd12d8934a3c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928055"
---
# <a name="how-to-debug-in-mixed-mode"></a>Como: Depurar no modo misto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os procedimentos a seguir descrevem como depurar código gerenciado e código nativo, também conhecido depuração de modo misto. Há dois cenários para fazer isso, dependendo de a DLL ou o aplicativo serem escritos em código nativo:  
  
-   O aplicativo de chamada que chama a DLL é escrito em código nativo. Nesse caso, a DLL é gerenciada e os depuradores gerenciados e nativos devem estar habilitados para depurar ambos. Você pode verificar isso na  **\<projeto > páginas de propriedade** caixa de diálogo. Como você faz isso depende de a depuração ser iniciada do projeto de DLL ou do projeto de aplicativo de chamada.  
  
-   O aplicativo de chamada que chama a DLL é escrito em código gerenciado e sua DLL é escrita em código nativo.  
  
> [!NOTE]
>  As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Para habilitar a depuração de modo misto  
  
1.  Na **Gerenciador de soluções**, selecione o projeto.  
  
2.  No menu **Exibir**, clique em **Páginas de Propriedades**.  
  
3.  No  **\<projeto > páginas de propriedades** caixa de diálogo caixa, expanda o **as propriedades de configuração** nó e, em seguida, selecione **depuração**.  
  
4.  Defina **Tipo de Depurador** como **Misto** ou **Automático**.  
  
## <a name="see-also"></a>Consulte também  
 [Como: Depurar por meio de um projeto DLL](../debugger/how-to-debug-from-a-dll-project.md)
