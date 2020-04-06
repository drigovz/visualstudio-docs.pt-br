---
title: Feedback para o Usuário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user model feedback
- environment, context
- IDE, context
- IDE, user feedback
ms.assetid: 2d472a24-3813-4f5f-9783-b491ad8a71ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46b9190b16b9aa444384847bf209ccca50c7f768
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708407"
---
# <a name="feedback-to-the-user"></a>Feedback para o usuário
No [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE), o feedback visual sobre a funcionalidade disponível é baseado na seleção atual do usuário e no contexto de seleção global. A tabela a seguir lista a funcionalidade disponível em diferentes contextos de seleção.

|Contexto de seleção|Funcionalidade disponível|
|-----------------------|-----------------------------|
|IDE|Global|
|Conjunto de produtos atuais|Específico do produto|
|Hierarquia ativa|Tipo de hierarquia específico|
|Item de hierarquia ativa|Tipo de item de hierarquia específico|
|Documento ativo|Tipo de documento específico|
|Janela MDI (Topmost multiple-document interface, interface de vários documentos) top|Tipo de janela específico|
|Contexto de seleção atual|Contexto de seleção específico|

 Se você só aparecer a funcionalidade que os usuários precisam e fornecer continuamente feedback consistente de seleção e contexto do ambiente, você reduz a complexidade no IDE. As seguintes regras se aplicam sempre que uma janela é aberta no IDE:

- Se a janela mudar seu contexto de seleção, o feedback de seleção será claramente indicado na janela, e a janela **Ajuda Dinâmica,** se mostrada, será atualizada para refletir o contexto atual.

- Se a janela mudar o contexto de seleção global, todos os menus específicos do contexto, a janela de hierarquia ativa e a barra de título do aplicativo serão atualizadas para refletir o contexto atual.

- A janela deve superfície satisfazer propriedades para a seleção atual na janela **Propriedades** e, opcionalmente, se exibida, a caixa de diálogo **Páginas** de propriedade.

- Se a janela não aparecer propriedades ou alterar o contexto de seleção global, o feedback de seleção não deve permanecer na janela quando não for mais a janela ativa no IDE.

- Todas as janelas de ferramentas específicas de documentos devem refletir continuamente o documento ativo.

- Menus, barras de ferramentas e a barra de título do aplicativo devem refletir a janela de cliente mdi (interface de vários documentos) mais alta.

  Por exemplo, quando a exibição HTML de um **Formulário Web** dentro de `<td>` um projeto de Aplicativo Web Básico Visual é aberta e o usuário seleciona uma tag, o feedback é fornecido da seguinte maneira:

- A seleção é indicada na janela ativa e refletida na janela **Propriedades.**

- A caixa de **ferramentas** específica do documento é atualizada para refletir o documento ativo.

- A barra de ferramentas **do Editor** e o menu **Tabela** são exibidos e as atualizações da barra de título para refletir a janela Formulário da Web.

- A janela de hierarquia ativa, que normalmente é **o Solution Explorer,** e sua atualização da barra de título para refletir o contexto atual e os comandos de menu **do Projeto** sensíveis ao contexto agora se aplicam ao projeto ativo do Aplicativo da Web.

## <a name="see-also"></a>Confira também
- [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md)
- [Hierarquias e seleção](../../extensibility/internals/hierarchies-and-selection.md)
