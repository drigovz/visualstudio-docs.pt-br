---
title: Nenhuma fonte disponível | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 69ea9c3a41f83b9c06dc18d6da1f859017f12ca5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697805"
---
# <a name="no-source-available"></a>Nenhuma origem disponível
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O projeto não contém código-fonte para o código que você está tentando exibir. A causa comum é clicar duas vezes em um módulo que não tem código-fonte na **Janela de Pilha de Chamadas** ou **Janela de Threads**. Você pode continuar a depuração, mas não pode usar a janela de origem para definir pontos de interrupção e executar outras ações nesse local. Se você precisar definir um ponto de interrupção, use a **Janela de Desmontagem**.  
  
 Nas Páginas de Propriedades de Solução, você pode alterar os diretórios em que o depurador procura arquivos de origens e informa o depurador para ignorar os arquivos de origem selecionados. Consulte [depurar arquivos de origem, propriedades comuns, caixa de diálogo páginas de propriedades da solução](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Navegar para localizar o código-fonte**  
 Clique neste link para abrir uma caixa de diálogo onde você pode procurar para localizar o código-fonte.  
  
 **Mostrar Desmontagem**  
 Inicia a **Janela de Desmontagem**.  
  
 **Sempre mostrar desmontagem para arquivos de origem ausentes**  
 Selecione esta opção para exibir **Janela de Desmontagem** automaticamente quando nenhuma origem estiver disponível. Essa configuração também pode ser alterada na caixa de diálogo **Opções**, categoria **Depuração**, página **Geral**, marcando ou desmarcando **Mostrar desmontagem se a fonte não estiver disponível**.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar arquivos de origem, propriedades comuns, caixa de diálogo páginas de propriedades da solução](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Especificar o símbolo (. pdb) e os arquivos de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll (extensão de depuração SOS)](https://msdn.microsoft.com/library/9ac1b522-77ab-4cdc-852a-20fcdc9ae498)
