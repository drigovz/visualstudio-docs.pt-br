---
title: Como especificar o binário para iniciar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: fd3379b9769cfd6bfe1335b12545e635a9bde782
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778681"
---
# <a name="how-to-specify-the-binary-to-start"></a>Como especificar o binário a ser iniciado

Para traçar o perfil de binários, como DLLs, você deve inserir informações na ** \<** caixa de diálogo Página> Páginas de Propriedade. Essa informação indica onde o projeto DLL pode localizar o aplicativo de chamada.

1. No **Gerenciador de Desempenho**, clique com o botão direito do mouse no binário de destino e, em seguida, clique em **Propriedades**.

2. Na caixa de diálogo **Páginas de Propriedades**, clique nas propriedades de **Inicialização**.

3. Selecione a caixa de seleção **Substituir as propriedades de projeto**.

4. Na caixa de texto **Executável a Ser Iniciado**, especifique o local do arquivo.

5. Na caixa de texto **Argumentos**, especifique os argumentos que são necessários para iniciar o aplicativo.

6. Na caixa de texto **Diretório de Trabalho**, especifique o local do diretório.

7. Clique em **OK**.

## <a name="see-also"></a>Confira também

[Configure sessões de desempenho](../profiling/configuring-performance-sessions.md)
