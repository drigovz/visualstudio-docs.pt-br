---
title: Assistentes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], providing wizard support
ms.assetid: 59d9a77f-ee80-474b-a14f-90f477ab717b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6e58ebd736f7bb9f35df6e41d5235f36f7037259
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687624"
---
# <a name="wizards"></a>Assistentes
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Depois de criar um assistente, você normalmente deseja adicioná-lo ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (ambiente de desenvolvimento integrado) para que outras pessoas possam usá-lo. O assistente adicionado é exibido nas caixas de diálogo **Adicionar novo projeto** ou **Adicionar novo item** . Para ver as caixas de diálogo **Adicionar novo projeto** ou **Adicionar novo item** , clique com o botão direito do mouse em uma solução aberta no **Gerenciador de soluções**, aponte para **Adicionar**e clique em **novo projeto** ou **novo item**.  
  
 Os assistentes podem ser implementados no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] para permitir que os usuários selecionem de um modo de exibição de árvore de valores disponíveis quando abrirem a caixa de diálogo **Adicionar novo projeto** ou a caixa de diálogo **Adicionar novo item** ou quando clicarem com o botão direito do mouse em um item no **Gerenciador de soluções**.  
  
 No assistente, você pode fornecer a opção de localizar o nome de um novo projeto ou ITES, e pode determinar o ícone que os usuários verão quando selecionarem o assistente. Você também pode controlar a ordem na qual novos itens aparecem em relação a outros itens disponíveis; os itens não precisam ser organizados em ordem alfabética.  
  
 Você também pode fornecer um assistente que começa de forma diferente, com base em parâmetros personalizados que são passados para o assistente quando ele é aberto.  
  
 Os tópicos nesta seção discutem os arquivos que você implementa para fazer com que as [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] caixas de diálogo **Adicionar novo projeto** e **Adicionar novo item** listem o assistente entre os assistentes e modelos disponíveis e os requisitos que o assistente deve atender para operar corretamente no IDE.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Arquivos de descrição do diretório de modelo (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)  
 Fornece uma visão geral de quais arquivos de descrição do diretório de modelo e explica como eles funcionam no IDE para exibir pastas, arquivos. vsz e arquivos de modelo associados a um projeto nas caixas de diálogo.  
  
 [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)  
 Explica como o IDE inicia os assistentes e lista as três partes do arquivo. vsz.  
  
 [Interface do assistente (IDTWizard)](../../extensibility/internals/wizard-interface-idtwizard.md)  
 Descreve a `IDTWizard` interface que os assistentes devem implementar para funcionar no IDE.  
  
 [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)  
 Explica como os assistentes são implementados e o que ocorre quando o IDE passa parâmetros de contexto para a implementação.  
  
 [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)  
 Explica como usar parâmetros personalizados para controlar a operação do assistente depois que o assistente é iniciado.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Tipos de Projeto](../../extensibility/internals/project-types.md)  
 Fornece links para tópicos adicionais que oferecem informações sobre como criar novos tipos de projeto.  
  
 [Instruções passo a passo: criando um assistente](https://msdn.microsoft.com/library/adb41fe9-fcca-4e87-bf4f-bf2fa68e8b06)  
 Ilustra como criar um assistente.  
  
 [Estender projetos](../../extensibility/extending-projects.md)  
 Descreve como usar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projetos e soluções para organizar arquivos de código e arquivos de recursos e como implementar o controle do código-fonte.
