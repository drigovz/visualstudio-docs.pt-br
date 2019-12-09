---
title: Criar minidespejos com todas as pilhas de chamadas
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 7d0580e04968a01dc8e447a9ee35f2b1c5934ccf
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461654"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Criar minidespejos para um processo do Visual Studio com todas as pilhas de chamadas

Em alguns casos, a Microsoft pode solicitar o minidespejo de um processo em execução do Visual Studio com informações de todas as pilhas de chamadas. Para coletar essas informações, execute estas etapas:

## <a name="create-the-minidump-file"></a>Criar o arquivo de minidespejo

1. Inicie uma nova instância do Visual Studio.
1. No menu principal, escolha **Depurar** > **Anexar ao Processo**.
1. Marque as caixas de seleção **Gerenciado** e **Nativo** relevantes e pressione **Anexar**.

   ![Anexar ao processo](../ide/media/attach-to-process.png)

1. Selecione a outra instância do Visual Studio a anexar na lista de processos em execução.
1. No menu principal, escolha **Depurar** > **Interromper Tudo**.
1. No menu principal, escolha **Depurar** > **Salvar Despejo Como**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Obter as pilhas de chamadas do minidespejo

1. Abra o arquivo de despejo no Visual Studio.
1. Vá para **Ferramentas** > **Opções** > **Depuração** > **Símbolo** e verifique se a caixa **Servidores de Símbolos Microsoft** está marcada nos **locais do arquivo de símbolos(.pdb)** .
1. Abra a janela **Comando** (**Exibição** > **Outras janelas** > **Janela de Comando**)
1. Digite '~*k'. A janela exibe as pilhas de chamadas de todos os threads.
1. Copie todo o texto da Janela de Comando e salve em um arquivo de texto.
1. Anexe o arquivo txt ao bug.
