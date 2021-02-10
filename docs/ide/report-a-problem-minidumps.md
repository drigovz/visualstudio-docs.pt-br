---
title: Criar minidespejos com todas as pilhas de chamadas
description: Saiba como criar minidespejos para um processo do Visual Studio que inclui informações para todas as pilhas de chamadas.
ms.custom: SEO-VS-2020
ms.date: 06/27/2019
ms.topic: how-to
helpviewer_keywords:
- minidumps for Visual Studio issues"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Collect minidumps to send to Microsoft for help with troubleshooting issues with Visual Studio
ms.openlocfilehash: 44ab0873580c7c541fc5e7fdde56cc1780929b75
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970771"
---
# <a name="create-minidumps-for-a-visual-studio-process-with-all-call-stacks"></a>Criar minidespejos para um processo do Visual Studio com todas as pilhas de chamadas

Em alguns casos, a Microsoft pode solicitar o minidespejo de um processo em execução do Visual Studio com informações de todas as pilhas de chamadas. Para coletar essas informações, execute estas etapas:

## <a name="create-the-minidump-file"></a>Criar o arquivo de minidespejo

1. Inicie uma nova instância do Visual Studio.
1. No menu principal, escolha **depurar**  >  **anexar ao processo**.
1. Marque as caixas de seleção **Gerenciado** e **Nativo** relevantes e pressione **Anexar**.

   ![Anexar ao processo](../ide/media/attach-to-process.png)

1. Selecione a outra instância do Visual Studio a anexar na lista de processos em execução.
1. No menu principal, escolha **depurar**  >  **interromper tudo**.
1. No menu principal, escolha **depurar**  >  **Salvar despejo como**.

## <a name="get-the-call-stacks-from-the-minidump"></a>Obter as pilhas de chamadas do minidespejo

1. Abra o arquivo de despejo no Visual Studio.
1. Vá para **ferramentas**  >  **Opções**  >  **depuração** de  >  **símbolos** e verifique se os **servidores de símbolos da Microsoft** estão marcados nos locais do arquivo de **símbolo (. pdb)**.
1. Abra a janela **Comando** (**Exibição** > **Outras janelas** > **Janela de Comando**)
1. Digite '~*k'. A janela exibe as pilhas de chamadas de todos os threads.
1. Copie todo o texto da Janela de Comando e salve em um arquivo de texto.
1. Anexe o arquivo txt ao bug.
