---
title: Usar o REPL do Node.js
description: O Visual Studio fornece suporte para interação com o runtime do Node.js
ms.date: 12/04/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9f13128bc552ffdb31b3f4a9315a3f9aa3543b0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962685"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Trabalhar com a janela interativa do Node.js

As Ferramentas Node.js para Visual Studio incluem uma janela interativa para o runtime do Node.js instalado. Essa janela permite que você insira o código JavaScript e veja os resultados imediatamente, bem como executar comandos npm para interagir com o projeto atual. A janela interativa também é conhecida como um REPL (**R** ead/**E** valuate/**P** rint **L** oop).

## <a name="open-the-interactive-window"></a>Abrir a janela interativa

Abra a janela interativa clicando com o botão direito do mouse no nó do projeto Node.js no Gerenciador de Soluções e selecionando **Abrir Janela Interativa do Node.js**.

![Janela interativa do Node.js no menu de contexto do projeto](../javascript/media/interactivewindow-open-from-project.png)

As chaves de curto-recorte padrão para abrir a Node.js janela interativa são **[Ctrl] + K, N**. Ou, você pode abrir a janela na barra de ferramentas escolhendo **Exibir**  >    >  **janela interativa** do WindowsNode.js.

## <a name="use-the-repl"></a>Usar o REPL

Depois de abrir a janela, você poderá inserir comandos.

![Janela interativa do Node.js](../javascript/media/interactivewindow.png)

A janela interativa tem vários comandos internos, que começam com um prefixo de ponto para diferenciá-los das funções JavaScript declaradas. Há suporte para os seguintes comandos:

**.cls, .clear** Limpa o conteúdo da janela do editor, deixando intactos o histórico e o contexto de execução.

**.help** Exibe a ajuda do comando especificado ou de todos os comandos disponíveis e as associações de teclas, caso nenhum seja especificado.

**.info** Mostra informações sobre o executável do Node.js atual usado.

**.npm** Executa um comando npm. Se a solução contiver mais de um projeto, especifique o projeto de destino usando `.npm [projectname] <npm arguments>`.

**.reset** Redefine o ambiente de execução para o estado inicial, mantendo o histórico.

**.save** Salva a sessão atual do REPL em um arquivo.