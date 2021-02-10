---
title: Nenhuma fonte disponível | Microsoft Docs
description: Saiba o que você pode fazer quando o projeto não tem código-fonte para o código que você deseja exibir.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e9993c4482d20393a3ca46d9afcd0a8ec1b13f65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942029"
---
# <a name="no-source-available"></a>Nenhuma origem disponível
O projeto não contém código-fonte para o código que você está tentando exibir. A causa comum é clicar duas vezes em um módulo que não tem código-fonte na **Janela de Pilha de Chamadas** ou **Janela de Threads**. Você pode continuar a depuração, mas não pode usar a janela de origem para definir pontos de interrupção e executar outras ações nesse local. Se você precisar definir um ponto de interrupção, use a **Janela de Desmontagem**.

 Nas Páginas de Propriedades de Solução, você pode alterar os diretórios em que o depurador procura arquivos de origens e informa o depurador para ignorar os arquivos de origem selecionados. Consulte [depurar arquivos de origem, propriedades comuns, caixa de diálogo páginas de propriedades da solução](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).

 **Procurar para localizar o código-fonte** Clique neste link para abrir uma caixa de diálogo onde você pode navegar para localizar o código-fonte.

 **Mostrar desmontagem** Inicia a **janela de desmontagem**.

 **Sempre mostrar desmontagem de arquivos de origem ausentes** Selecione esta opção para exibir a **janela de desmontagem** automaticamente quando nenhuma fonte estiver disponível. Essa configuração também pode ser alterada na caixa de diálogo **Opções**, categoria **Depuração**, página **Geral**, marcando ou desmarcando **Mostrar desmontagem se a fonte não estiver disponível**.

## <a name="see-also"></a>Consulte também
- [Depurar arquivos de origem, propriedades comuns, caixa de diálogo páginas de propriedades da solução](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)
- [Especificar os arquivos de origem e símbolo (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [SOS.dll (extensão de depuração SOS)](/dotnet/framework/tools/sos-dll-sos-debugging-extension)