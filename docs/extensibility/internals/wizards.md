---
title: Magos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d65cf2dcc10380b0ac750c8e1b0e7fd56eab95b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703203"
---
# <a name="wizards"></a>Assistentes
Depois de criar um assistente, você normalmente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deseja adicioná-lo ao ambiente de desenvolvimento integrado (IDE) para que outros possam usá-lo. Em seguida, o assistente adicionado é exibido nas caixas de diálogo **Adicionar novo projeto** ou adicionar novo **item.** Para ver o **Adicionar novo projeto** ou adicionar caixas de diálogo de novo **item,** clique com o botão direito do mouse em uma solução aberta no **Solution Explorer**, aponte para **Adicionar**e clique em **Novo Projeto** ou **Novo Item**.

 Os assistentes podem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ser implementados para permitir que os usuários selecionem a partir de uma exibição de árvore de valores disponíveis quando abrem a caixa de diálogo **Adicionar novo projeto** ou a caixa de diálogo Adicionar novo **item,** ou quando clicarem com o botão direito do mouse em um item no **Solution Explorer**.

 No seu assistente, você pode fornecer a opção de localizar o nome de um novo projeto ou ites, e você pode determinar o ícone que os usuários verão quando selecionaro assistente. Você também pode controlar a ordem em que novos itens aparecem em relação a outros itens disponíveis; os itens não têm que ser organizados alfabeticamente.

 Você também pode fornecer um assistente que começa de forma diferente, com base em parâmetros personalizados que são passados para o assistente quando ele é aberto.

 Os tópicos desta seção discutem os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] arquivos que você implementa para causar as caixas de diálogo **Adicionar novo projeto** e adicionar novo **item** para listar seu assistente entre os assistentes e modelos disponíveis e os requisitos que seu assistente deve atender para operar corretamente no IDE.

## <a name="in-this-section"></a>Nesta seção
- [Arquivos de descrição do diretório de modelo (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

 Fornece uma visão geral de quais arquivos de descrição do diretório de modelos e explica como eles funcionam no IDE para exibir pastas, arquivos assistente .vsz e arquivos de modelo que estão associados a um projeto nas caixas de diálogo.

- [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)

 Explica como o IDE inicia assistentes e lista as três partes do arquivo .vsz.

- [Interface do assistente (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)

 Descreve a `IDTWizard` interface que os assistentes devem implementar para trabalhar no IDE.

- [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)

 Explica como os assistentes são implementados e o que ocorre quando o IDE passa parâmetros de contexto para a implementação.

- [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)

 Explica como usar parâmetros personalizados para controlar o funcionamento do assistente após o início do assistente.

## <a name="related-sections"></a>Seções relacionadas
- [Tipos de projeto](../../extensibility/internals/project-types.md)

 Fornece links para tópicos adicionais que oferecem informações sobre como projetar novos tipos de projetos.

- [Estender projetos](../../extensibility/extending-projects.md)

 Descreve como usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projetos e soluções para organizar arquivos de código e arquivos de recursos e como implementar o controle de origem.
