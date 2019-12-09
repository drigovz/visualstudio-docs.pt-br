---
title: Como exibir documentos de script | Microsoft Docs
ms.date: 11/05/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5e362e0504c4ed2584bbbbea687fe3c58fc79edb
ms.sourcegitcommit: ba0fef4f5dca576104db9a5b702670a54a0fcced
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73714432"
---
# <a name="how-to-view-script-documents-javascript"></a>Como exibir documentos de script (JavaScript)

Os arquivos de script do lado do servidor são visíveis no Gerenciador de Soluções. Os arquivos de script do lado do cliente são visíveis apenas quando você está no modo de depuração ou modo de interrupção. Os arquivos de script do lado do cliente são exibidos no nó **documentos de script** .

Para alguns tipos de aplicativos que geram dinamicamente páginas, é mais fácil entrar no modo de interrupção e depurar quando você define um ponto de interrupção de um documento de script que é carregado no navegador. Da mesma forma, você pode adicionar a instrução `debugger` de um documento de script carregado para entrar no modo de interrupção. Este artigo mostra como exibir esses documentos.

> [!NOTE]
> Anterior ao [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], os arquivos de script do lado do cliente gerados a partir do script do lado do servidor apareciam na janela do Gerenciador de script.

### <a name="to-view-a-server-side-script-document"></a>Para exibir um documento de script do lado do servidor

1. No **Gerenciador de Soluções**, abra o nó **\<<Nome do caminho do site>** .

2. Clique duas vezes no arquivo de script que deseja exibir.

     O arquivo de script do lado do servidor é aberto em uma janela de origem.

### <a name="to-view-a-client-side-script-document"></a>Para exibir um documento de script do lado do cliente

1. No **Gerenciador de Soluções**, abra o nó **Documentos de Script**.

2. Clique duas vezes no arquivo de script que deseja exibir.

     O arquivo de script do lado do cliente é aberto em uma janela de origem.

## <a name="see-also"></a>Consulte também
- [Exibindo dados no depurador](../debugger/viewing-data-in-the-debugger.md)