---
title: Guia geral, caixa de diálogo de propriedades de janela | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 455706670424bdeb1119036df98bac91e6cc9355
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018745"
---
# <a name="general-tab-window-properties-dialog-box"></a>Guia Geral, Caixa de diálogo Propriedades da Janela
Use o **geral** guia para mostrar informações sobre a janela selecionada. Para exibir o [janela caixa de diálogo de propriedades](../debugger/window-properties-dialog-box.md), mova o foco para o [modo de exibição do Windows](../debugger/windows-view.md) janela. Selecione qualquer nó de janela na árvore e escolha **propriedades** da **exibição** menu.  
  
 As seguintes configurações estão disponíveis sobre o **geral** guia:  
  
|Entrada|Descrição|  
|-----------|-----------------|  
|**Legenda da Janela**|O texto na legenda da janela, ou o texto contido em uma janela se ele for um controle.|  
|**Identificador da Janela**|A ID exclusiva dessa janela. Os números de identificador de janela são reutilizados; elas identificam uma janela somente para o tempo de vida dessa janela.|  
|**Procedimento de Janela**|O endereço virtual da função de procedimento de janela para esta janela. Este campo também indica se essa janela é uma janela de Unicode e seja subclasse.|  
|**Retângulo**|O retângulo delimitador para a janela. O tamanho do retângulo também é exibido. As unidades são pixels em coordenadas da tela.|  
|**Retângulo Restaurado**|O retângulo delimitador para a janela restaurado. O tamanho do retângulo também é exibido. Retângulo restaurado será diferente de retângulo somente quando a janela é maximizada ou minimizada. As unidades são pixels em coordenadas da tela.|  
|**Retângulo do Cliente**|O retângulo delimitador para a área de cliente da janela. O tamanho do retângulo também é exibido. As unidades são pixels relativos ao canto superior esquerdo da área de cliente da janela.|  
|**Identificador de Instância**|O identificador da instância do aplicativo. Identificadores de instância não são exclusivos.|  
|**ID de controle ou o identificador de Menu**|Se a janela que está sendo exibido é uma janela filho, o rótulo de identificação de controle é exibido. ID do controle é um inteiro que identifica ID de controle. desta janela filho Se a janela que está sendo exibido não for uma janela filho, o rótulo de tratar de Menu é exibido. Identificador de menu é um inteiro que identifica o identificador do menu associado a esta janela.|  
|**Dados de Usuário**|Dados específicos do aplicativo que estão anexados a essa estrutura de janela.|  
|**Bytes da Janela**|O número de bytes adicionais associados a esta janela. O significado desses bytes é determinado pelo aplicativo. Expanda a caixa de lista para ver os valores de byte em formato DWORD.|