---
title: 'Como: Iniciar o Spy + + | Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85e253491a4cb3713b5920c9abd09f9396298319
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099137"
---
# <a name="how-to-start-spy"></a>Como: Iniciar Spy++

Você pode iniciar o Spy + + do Visual Studio ou em um prompt de comando.

 Ao iniciar o Spy + +, se uma mensagem é exibida para solicitar permissão para fazer alterações no computador, selecione **Sim**.

> [!NOTE]
>  Você pode executar apenas uma instância do Spy + +. Se você tentar iniciar uma segunda instância, ele apenas faz com que a instância em execução no momento obter o foco.

## <a name="prerequisites"></a>Pré-requisitos

Spy + + requer os seguintes componentes. Você pode selecionar esses componentes do instalador do Visual Studio, selecionando o **componentes individuais** guia e, em seguida, selecionando os componentes a seguir.

* Em depuração e testes, selecione  **C++ ferramentas de criação de perfil**
* Em atividades de desenvolvimento, selecione **Visual Studio C++ recursos principais**

Se você tiver feito alterações, siga os prompts para instalar esses componentes.

## <a name="start-spy-from-visual-studio"></a>Iniciar o Spy + + do Visual Studio

Sobre o **ferramentas** menu, selecione **Spy + +**.

Como o Spy + + é executado de forma independente, depois de iniciada, você pode fechar o Visual Studio.

> [!NOTE]
>  Quando você registra mensagens com Spy + +, pode fazer com que o sistema operacional executar mais lentamente.

## <a name="start-spy-at-a-command-prompt"></a>Iniciar o Spy + + em um prompt de comando

1. Em uma janela de Prompt de comando, altere os diretórios para a pasta que contém spyxx.exe. Normalmente, o caminho para essa pasta é... \\ *Pasta de instalação do visual Studio*\Common7\Tools\\.

2. Insira **spyxx.exe**.

## <a name="see-also"></a>Consulte também
- [Usando Spy++](../debugger/using-spy-increment.md)
- [Exibições do Spy++](../debugger/spy-increment-views.md)
- [Referência a Spy++](../debugger/spy-increment-reference.md)