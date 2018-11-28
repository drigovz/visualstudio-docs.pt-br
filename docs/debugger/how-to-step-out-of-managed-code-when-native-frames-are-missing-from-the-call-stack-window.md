---
title: 'Como: sair do código gerenciado quando quadros nativos estiverem ausentes da janela pilha de chamadas | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e5c671f93e20da108a9fd1069a0950f52ef00da9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388563"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Como sair do código gerenciado quando quadros nativos não forem encontrados na janela Pilha de Chamadas

Se seu código tiver quadros nativos que são invisíveis na janela Pilha de Chamadas **, depurar fora do código gerenciado pode produzir resultados inesperados. Como alternativa, você poderá usar um ponto de interrupção em vez de Depuração Circular **.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas. Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**. Para obter mais informações, consulte [redefinir configurações](../ide/environment-settings.md#reset-settings).

## <a name="step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Para depurar fora do código gerenciado quando os quadros nativos estiverem ausentes da exibição da pilha de chamadas

1.  No código nativo, defina um ponto de interrupção do local depois da chamada para o código gerenciado.

2.  No menu Depurar **, escolha Continuar**.

     Quando a chamada gerenciada for concluída, a execução será interrompida no ponto de interrupção no código nativo.

## <a name="see-also"></a>Consulte também

- [Como usar a janela Pilha de Chamadas](../debugger/how-to-use-the-call-stack-window.md)