---
title: Seleção e Moeda no IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705578"
---
# <a name="selection-and-currency-in-the-ide"></a>Seleção e moeda no IDE
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) mantém informações sobre os objetos selecionados atualmente pelos usuários usando *o contexto*de seleção . Com o contexto de seleção, os VSPackages podem participar do rastreamento de moedas de duas maneiras:

- Ao propagar informações de moeda sobre os VSPackages para o IDE.

- Monitorando as seleções ativas atualmente dos usuários dentro do IDE.

## <a name="selection-context"></a>Contexto de seleção
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE mantém globalmente o controle da moeda IDE em seu próprio objeto de contexto de seleção global. A tabela a seguir mostra os elementos que compõem o contexto de seleção.

|Elemento|Descrição|
|-------------|-----------------|
|Hierarquia atual|Tipicamente o projeto atual; uma hierarquia de corrente NULL indica que a solução como um todo é atual.|
|ItemID atual|O item selecionado na hierarquia atual; quando há várias seleções em uma janela de projeto, pode haver vários itens atuais.|
|Atual`SelectionContainer`|Segura um ou mais objetos para os quais a janela Propriedades deve exibir propriedades.|

 Além disso, o ambiente mantém duas listas globais:

- Uma lista de identificadores ativos de comando ui

- Uma lista de tipos de elementos ativos atualmente.

### <a name="window-types-and-selection"></a>Tipos de janelas e seleção
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organiza janelas em dois tipos gerais:

- Janelas do tipo hierarquia

- Janelas de moldura, como janelas de ferramentas e documentos

  O IDE rastreia a moeda de forma diferente para cada um desses tipos de janelas.

  A janela mais comum do tipo de projeto é o explorador de soluções, que o IDE controla. Uma janela do tipo projeto rastreia a hierarquia global e o ItemID do contexto de seleção global, e a janela depende da seleção do usuário para determinar a hierarquia atual. Para janelas do tipo projeto, o <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>ambiente fornece o serviço global, através do qual o VSPackages pode monitorar os valores atuais para elementos abertos. A navegação de propriedade no ambiente é impulsionada por este serviço global.

  As janelas de quadro, por outro lado, usam o DocObject dentro da janela do quadro para pressionar o valor SelectionContext (o trio hierarchy/ItemID/SelectionContainer). . Janelas de moldura <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> usam o serviço para este fim. O DocObject pode empurrar apenas valores para o contêiner de seleção, deixando os valores locais para hierarquia e ItemID inalterados, como é típico para documentos de criança SMDI.

### <a name="events-and-currency"></a>Eventos e Moeda
 Dois tipos de eventos podem ocorrer que afetam a noção de moeda do ambiente:

- Eventos que são propagados para o nível global e alteram o contexto de seleção de quadros de janela. Exemplos desse tipo de evento incluem a abertura de uma janela MDI Child, a abertura de uma janela global de ferramentas ou a abertura de uma janela de ferramenta do tipo projeto.

- Eventos que alteram os elementos traçados no contexto de seleção do quadro da janela. Exemplos incluem alterar a seleção dentro de um DocObject ou alterar a seleção em uma janela do tipo projeto.

## <a name="see-also"></a>Confira também
- [Objetos de contexto da seleção](../../extensibility/internals/selection-context-objects.md)
- [Comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md)
