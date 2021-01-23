---
title: Especificar o binário para iniciar | Microsoft Docs
description: Saiba como você deve inserir informações na <Target> caixa de diálogo páginas de propriedades para os binários de perfil, como DLLs.
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 715c92a26ae33a4e909ec737c866be1cdc15251e
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98721834"
---
# <a name="how-to-specify-the-binary-to-start"></a>Como especificar o binário a ser iniciado

Para criar perfis de binários, como DLLs, você deve inserir informações na caixa de diálogo **\<Target> páginas de propriedades** . Essa informação indica onde o projeto DLL pode localizar o aplicativo de chamada.

1. No **Gerenciador de Desempenho**, clique com o botão direito do mouse no binário de destino e, em seguida, clique em **Propriedades**.

2. Na caixa de diálogo **Páginas de Propriedades**, clique nas propriedades de **Inicialização**.

3. Selecione a caixa de seleção **Substituir as propriedades de projeto**.

4. Na caixa de texto **Executável a Ser Iniciado**, especifique o local do arquivo.

5. Na caixa de texto **Argumentos**, especifique os argumentos que são necessários para iniciar o aplicativo.

6. Na caixa de texto **Diretório de Trabalho**, especifique o local do diretório.

7. Clique em **OK**.

## <a name="see-also"></a>Confira também

[Configurar sessões de desempenho](../profiling/configuring-performance-sessions.md)
