---
title: 'Como: Exibir documentos de Script | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3592056fdde7756f3fbe63d0dc5d86782fdf9a8b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867716"
---
# <a name="how-to-view-script-documents"></a>Como: Exibir documentos de script
Em versões anteriores do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], os arquivos de script do lado do cliente gerados do script do lado do servidor eram exibidos na janela Explorador de Script. A janela Explorador de Script estava geralmente oculta, de modo que a disponibilidade de script do lado do cliente não era sempre óbvia.  
  
 No [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], os arquivos de script do lado do cliente gerados do script do lado do servidor aparecem no Gerenciador de Soluções, que é visível por padrão. A janela Explorador de Script foi eliminada.  
  
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