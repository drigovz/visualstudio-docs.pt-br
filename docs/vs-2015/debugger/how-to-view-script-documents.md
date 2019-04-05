---
title: 'Como: Exibir documentos de Script | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cadfa9cf4c07b84f8e0f4c00678a858876c25bd0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928706"
---
# <a name="how-to-view-script-documents"></a>Como: Exibir documentos de script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Em versões anteriores do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], os arquivos de script do lado do cliente gerados do script do lado do servidor eram exibidos na janela Explorador de Script. A janela Explorador de Script estava geralmente oculta, de modo que a disponibilidade de script do lado do cliente não era sempre óbvia.  
  
 No [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], os arquivos de script do lado do cliente gerados do script do lado do servidor aparecem no Gerenciador de Soluções, que é visível por padrão. A janela Explorador de Script foi eliminada.  
  
 Os arquivos de script do lado do cliente são visíveis apenas quando você está no modo de depuração ou modo de interrupção. Eles aparecem no nó **Documentos de Script**.  
  
 Os arquivos de script do lado do servidor são sempre visíveis. Eles aparecem no nó **\<<Nome do caminho do site>**. O nome do nó é semelhante a este exemplo: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Para exibir um documento de script do lado do servidor  
  
1.  No **Gerenciador de Soluções**, abra o nó **\<<Nome do caminho do site>**.  
  
2.  Clique duas vezes no arquivo de script que deseja exibir.  
  
     O arquivo de script do lado do servidor é aberto em uma janela de origem.  
  
### <a name="to-view-a-client-side-script-document"></a>Para exibir um documento de script do lado do cliente  
  
1.  No **Gerenciador de Soluções**, abra o nó **Documentos de Script**.  
  
2.  Clique duas vezes no arquivo de script que deseja exibir.  
  
     O arquivo de script do lado do cliente é aberto em uma janela de origem.  
  
## <a name="see-also"></a>Consulte também  
 [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)
