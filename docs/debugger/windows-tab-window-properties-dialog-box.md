---
title: Guia Windows, caixa de diálogo Propriedades da janela | Microsoft Docs
description: Use a guia Windows das propriedades do Windows para mostrar informações sobre as janelas relacionadas à janela selecionada. Consulte este artigo para ver as configurações.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffc7f8a80e86779f2cc419f841a3b80280f39c9e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896397"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Guia Janelas, Caixa de diálogo Propriedades da Janela
Use a guia **Windows** para mostrar informações sobre o Windows relacionadas à janela selecionada. Para exibir a [caixa de diálogo Propriedades da janela](../debugger/window-properties-dialog-box.md), mova o foco para a janela [exibição do Windows](../debugger/windows-view.md) . Selecione qualquer nó de janela na árvore e, em seguida, escolha **Propriedades** no menu **Exibir** .

 As configurações a seguir estão disponíveis na guia **Windows** :

|Entrada|Descrição|
|-----------|-----------------|
|**Próxima janela**|O identificador da próxima janela irmã na mesma sequência (ordem Z) mostrada no modo de exibição de árvore de janela ("nenhum" se não houver nenhuma janela seguinte). Escolha esta entrada para exibir as propriedades da próxima janela.|
|**Janela anterior**|O identificador da janela irmã anterior na mesma sequência (ordem Z) mostrada no modo de exibição de árvore de janela ("None" se não houver nenhuma janela anterior). Escolha esta entrada para exibir as propriedades da janela anterior.|
|**Janela pai**|O identificador da janela pai desta janela ("None" se não houver nenhum pai). Escolha esta entrada para exibir as propriedades da janela pai.|
|**First Child**|O identificador da primeira janela filho da janela, na sequência (ordem Z) mostrada no modo de exibição de árvore da janela ("nenhum" se não houver nenhuma janela filho). Escolha esse valor para exibir as propriedades da primeira janela filho.|
|**Janela Proprietário**|O identificador da janela do proprietário da janela. A janela principal de um aplicativo normalmente possui janelas de diálogo modais do sistema, por exemplo ("nenhum" se não houver nenhum proprietário). Escolha esta entrada para exibir as propriedades da janela do proprietário.|