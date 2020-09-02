---
title: Guia geral, caixa de diálogo Propriedades da janela | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3b8733ef63a60baa1b268c42c8780cdf80f2674b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159956"
---
# <a name="general-tab-window-properties-dialog-box"></a>Guia Geral, Caixa de diálogo Propriedades da Janela
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Use a guia **geral** para mostrar informações sobre a janela selecionada. Para exibir a [caixa de diálogo Propriedades da janela](../debugger/window-properties-dialog-box.md), mova o foco para a janela [exibição do Windows](../debugger/windows-view.md) . Selecione qualquer nó de janela na árvore e, em seguida, escolha **Propriedades** no menu **Exibir** .  
  
 As configurações a seguir estão disponíveis na guia **geral** :  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Legenda da Janela**|O texto na legenda da janela ou texto contido em uma janela, se for um controle.|  
|**Identificador da Janela**|A ID exclusiva desta janela. Os números de identificador de janela são reutilizados; eles identificam uma janela somente pelo tempo de vida dessa janela.|  
|**Procedimento de Janela**|O endereço virtual da função de procedimento de janela para esta janela. Esse campo também indica se esta janela é Unicode e se ela está em uma subclasse.|  
|**Retângulo**|O retângulo delimitador para a janela. O tamanho do retângulo também é exibido. As unidades são pixels em coordenadas de tela.|  
|**Retângulo Restaurado**|O retângulo delimitador para a janela restaurada. O tamanho do retângulo também é exibido. O Rect restaurado será diferente do retângulo somente quando a janela for maximizada ou minimizada. As unidades são pixels em coordenadas de tela.|  
|**Retângulo do Cliente**|O retângulo delimitador para a área de cliente da janela. O tamanho do retângulo também é exibido. As unidades são pixels em relação à parte superior esquerda da área do cliente da janela.|  
|**Identificador de Instância**|O identificador de instância do aplicativo. Os identificadores de instância não são exclusivos.|  
|**ID de controle ou identificador de menu**|Se a janela que está sendo exibida for uma janela filho, o rótulo de ID de controle será exibido. ID de controle é um inteiro que identifica a ID de controle da janela filho. Se a janela que está sendo exibida não for uma janela filho, o rótulo do identificador de menu será exibido. O identificador de menu é um inteiro que identifica o identificador do menu associado a esta janela.|  
|**Dados do usuário**|Dados específicos do aplicativo anexados a esta estrutura de janela.|  
|**Bytes da Janela**|O número de bytes extras associados a esta janela. O significado desses bytes é determinado pelo aplicativo. Expanda a caixa de listagem para ver os valores de byte no formato DWORD.|
