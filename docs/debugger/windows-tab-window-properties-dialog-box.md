---
title: Guia do Windows, a janela caixa de diálogo de propriedades | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, Windows Tab
ms.assetid: 9001342a-09a8-4f5e-b6ed-881a3b9d7246
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce1015741b2a1e7ba1608eea7f198b726e808f7f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62900777"
---
# <a name="windows-tab-window-properties-dialog-box"></a>Guia Janelas, Caixa de diálogo Propriedades da Janela
Use o **Windows** guia para exibir informações sobre windows relacionados a janela selecionada. Para exibir o [janela caixa de diálogo de propriedades](../debugger/window-properties-dialog-box.md), mova o foco para o [modo de exibição do Windows](../debugger/windows-view.md) janela. Selecione qualquer nó de janela na árvore e escolha **propriedades** da **exibição** menu.

 As seguintes configurações estão disponíveis sobre o **Windows** guia:

|Entrada|Descrição|
|-----------|-----------------|
|**Próxima janela**|O identificador da janela próximo irmão na mesma sequência (ordem Z) mostrada na exibição de árvore de janela ("none" se não houver nenhuma janela próximo). Escolha essa entrada para exibir as propriedades da janela próximo.|
|**Janela anterior**|O identificador da janela de irmão anterior na mesma sequência (ordem Z) mostrada na exibição de árvore de janela ("none" se não houver nenhuma janela anterior). Escolha essa entrada para exibir as propriedades da janela anterior.|
|**Janela pai**|O identificador da janela de pai dessa janela ("none" se não houver nenhum pai). Escolha essa entrada para exibir as propriedades da janela pai.|
|**Primeiro filho**|O identificador da primeira janela filho dessa janela, na sequência (ordem Z) mostrado na exibição de árvore de janela ("none" se não houver nenhuma janela filho). Escolha esse valor para exibir as propriedades da primeira janela filho.|
|**Janela Proprietário**|O identificador da janela do proprietário dessa janela. Janela principal do aplicativo normalmente possui windows da caixa de diálogo modal do sistema, por exemplo ("none" se não houver nenhum proprietário). Escolha essa entrada para exibir as propriedades da janela do proprietário.|