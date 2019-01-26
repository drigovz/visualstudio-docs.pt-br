---
title: 'Como: Atualizar a barra de Status | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - update status bar
ms.assetid: 7500c8a7-4913-4818-a88b-bfd1b9887cb6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49661e379c81bac935e2d2ae2279e32d548eb698
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929868"
---
# <a name="how-to-update-the-status-bar"></a>Como: Atualizar a barra de Status
O **barra de Status** uma barra de controle que está localizada na parte inferior de muitas janelas de aplicativo que contém um ou mais linhas de texto de status ou indicadores.  
  
## <a name="to-update-the-status-bar"></a>Para atualizar a barra de Status  
  
1.  Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> em cada objeto de exibição individual (DocView) que fornece seu editor, como uma exibição de formulário e um modo de exibição de código.  
  
2.  Quando chama o IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A>, atualize as informações de **barra de Status** chamando os métodos de <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser>.  
  
    > [!NOTE]
    >  As chamadas IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> somente quando a janela de documento for ativada inicialmente. Para o restante do tempo que sua janela do documento está ativa, você deve atualizar o **barra de Status** informações como o estado de suas alterações de editor.  
  
## <a name="robust-programming"></a>Programação robusta  
 Um **barra de Status** contém quatro campos separados:  
  
- Texto de status  
  
- Barra de progresso  
  
- Ícone animado  
  
- Informações do Editor  
  
  Para obter mais informações, consulte [barras de Status](/cpp/mfc/status-bars).  
  
  O IDE chama automaticamente o <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> método de sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> implementação quando a janela de documento é ativada.  
  
  O implementador de VSPackage é responsável por atualizar o texto de status na barra de status. O IDE redefine essa cadeia de caracteres para "Pronto" se o campo de texto de status é definido como texto vazio ("") no tempo ocioso.  
  
## <a name="see-also"></a>Consulte também  
 [Barras de status](/cpp/mfc/status-bars)