---
title: Nenhuma origem disponível | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.nosource
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- No Source Code Available for the Current Location dialog box
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d1d1307a119fa23bf7ba015130ab9c7b6f69d5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905213"
---
# <a name="no-source-available"></a>Nenhuma origem disponível
O projeto não contém código-fonte para o código que você está tentando exibir. A causa comum é clicar duas vezes em um módulo que não tem código-fonte na **Janela de Pilha de Chamadas** ou **Janela de Threads**. Você pode continuar a depuração, mas não pode usar a janela de origem para definir pontos de interrupção e executar outras ações nesse local. Se você precisar definir um ponto de interrupção, use a **Janela de Desmontagem**.

 Nas Páginas de Propriedades de Solução, você pode alterar os diretórios em que o depurador procura arquivos de origens e informa o depurador para ignorar os arquivos de origem selecionados. Ver [caixa de diálogo de páginas de propriedade do código-fonte arquivos, propriedades comuns, solução de depuração](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Navegue para localizar o código-fonte** clique neste link para abrir uma caixa de diálogo onde você pode procurar para localizar o código-fonte.

 **Mostrar desmontagem** inicia o **janela de desmontagem**.

 **Sempre Mostrar desmontagem para arquivos de origem ausentes** Selecione esta opção para exibir o **janela de desmontagem** automaticamente quando nenhuma origem estiver disponível. Essa configuração também pode ser alterada na caixa de diálogo **Opções**, categoria **Depuração**, página **Geral**, marcando ou desmarcando **Mostrar desmontagem se a fonte não estiver disponível**.

## <a name="see-also"></a>Consulte também
- [Caixa de diálogo Depurar Arquivos de Origem, Propriedades Comuns, Páginas de Propriedades da Solução](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (Extensão de Depuração SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)