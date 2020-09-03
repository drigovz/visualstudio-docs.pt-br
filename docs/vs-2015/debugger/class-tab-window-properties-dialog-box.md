---
title: Guia classe, caixa de diálogo Propriedades da janela | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, Class Tab
ms.assetid: eaec9f07-d580-436d-934d-76c4e59439aa
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a7f81a100b2c2311444732434df0f5c5599742a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161607"
---
# <a name="class-tab-window-properties-dialog-box"></a>Guia Classe, Caixa de diálogo Propriedades da Janela
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use a guia **classe** para mostrar informações sobre a classe da janela selecionada. Para exibir a [caixa de diálogo Propriedades da janela](../debugger/window-properties-dialog-box.md), mova o foco para a janela [exibição do Windows](../debugger/windows-view.md) . Selecione qualquer nó de janela na árvore e, em seguida, escolha **Propriedades** no menu **Exibir** .  
  
 As configurações a seguir estão disponíveis na guia **classe** :  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Nome da classe**|O nome (ou número ordinal) dessa classe de janela.|  
|**Estilos de Classe**|Uma combinação de códigos de estilo de classe.|  
|**Bytes da Classe**|Dados específicos do aplicativo associados a esta classe de janela.|  
|**Átomo da Classe**|O Atom para a classe retornada pela chamada **registerClass** .|  
|**Identificador de Instância**|O identificador de instância do módulo que registrou a classe. Os identificadores de instância não são exclusivos.|  
|**Bytes da Janela**|O número de bytes extras associados a cada janela dessa classe. O significado desses bytes é determinado pelo aplicativo. Expanda a caixa de listagem para ver os valores de byte no formato DWORD.|  
|**Procedimento de Janela**|O endereço atual da função **WndProc** para Windows desta classe. Isso difere do **proc de janela** na guia **geral** se a janela estiver em uma subclasse.|  
|**Nome do Menu**|O nome do menu principal que está associado ao Windows desta classe ("None" se não houver nenhum menu).|  
|**Identificador de Ícone**|O identificador do ícone associado ao Windows desta classe ("None" se não houver nenhum ícone).|  
|**Identificador de Cursor**|O identificador do cursor associado ao Windows desta classe ("None" se não houver um cursor).|  
|**Pincel da Tela de Fundo**|O identificador do pincel de plano de fundo que está associado ao Windows desta classe ou uma das cores predefinidas COLOR_ * para pintar o plano de fundo da janela ("nenhum" se não houver um pincel).|
