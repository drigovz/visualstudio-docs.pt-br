---
title: 'Como: atualizar a barra de status | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1d48b07dd5e4fc1fe745e3669041884c1b8eacd9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703142"
---
# <a name="how-to-update-the-status-bar"></a>Como atualizar a barra de status
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A **barra de status** é uma barra de controle localizada na parte inferior de muitas janelas de aplicativo que contêm uma ou mais linhas ou indicadores de texto de status.  
  
### <a name="to-update-the-status-bar"></a>Para atualizar a barra de status  
  
1. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> em cada objeto de exibição individual (DocView) que seu editor fornece, como uma exibição de formulário e uma exibição de código.  
  
2. Quando o IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> , atualize as informações na **barra de status** chamando os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> .  
  
    > [!NOTE]
    > O IDE chama <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> apenas quando a janela do documento é ativada inicialmente. Para o restante da hora em que a janela do documento está ativa, você deve atualizar as informações da **barra de status** conforme o estado do seu editor é alterado.  
  
## <a name="robust-programming"></a>Programação robusta  
 Uma **barra de status** contém quatro campos separados:  
  
- Texto de status  
  
- Barra de progresso  
  
- Ícone animado  
  
- Informações do editor  
  
  Para obter mais informações, consulte [barras de status](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e).  
  
  O IDE chama automaticamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método de sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementação quando a janela do documento é ativada.  
  
  O implementador VSPackage é responsável por atualizar o texto de status na barra de status. O IDE redefine essa cadeia de caracteres para "pronto" se o campo de texto status for definido como texto vazio ("") no tempo ocioso.  
  
## <a name="see-also"></a>Consulte Também  
 [Barras de status](https://msdn.microsoft.com/library/fcbc5029-1aab-4e14-adf7-419038a4935e)
