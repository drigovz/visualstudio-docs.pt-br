---
title: Arquitetura plug-in de controle de fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f549ad2c4ee456860a08fbf20ccda813934a8582
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705103"
---
# <a name="source-control-plug-in-architecture"></a>Arquitetura do plug-in de controle do código-fonte
Você pode adicionar suporte [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ao controle de origem ao ambiente de desenvolvimento integrado (IDE) implementando e anexando um plug-in de controle de origem. O IDE conecta-se ao plug-in de controle de origem através da Bem definida API plug-in de controle de fonte. O IDE expõe os recursos de controle de versão do sistema de controle de origem, fornecendo uma interface de usuário (UI) que consiste em barras de ferramentas e comandos de menu. O plug-in de controle de origem implementa a funcionalidade de controle de origem.

## <a name="source-control-plug-in-resources"></a>Recursos de plug-in de controle de fonte
 O Plug-in de controle de origem fornece recursos para [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ajudar a criar e conectar seu aplicativo de versão ao IDE. O Plug-in de controle de origem contém a especificação da API que deve ser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementada por um plug-in de controle de origem para que possa ser integrado ao IDE. Ele também contém uma amostra de código (escrita em C++) que implementa um plug-in de controle de origem esqueleto demonstrando a implementação de funções essenciais compatíveis com a API plug-in de controle de fonte.

 A especificação da API plug-in de controle de origem permite que você aproveite qualquer sistema de controle de origem de sua escolha se você criar um DLL de controle de origem com o conjunto de funções necessárias implementado de acordo com a API de controle de fonte.

## <a name="components"></a>Componentes
 O Pacote adaptador de controle de origem no diagrama é o componente do IDE que traduz a solicitação do usuário para uma operação de controle de origem em uma chamada de função suportada pelo plug-in de controle de origem. Para que isso aconteça, o IDE e o plug-in de controle de origem devem ter uma diálogo eficaz que passe informações para frente e para trás entre o IDE e o plug-in. Para que esse diálogo ocorra, ambos devem falar a mesma língua. A API plug-in de controle de origem descrita nesta documentação é o vocabulário comum para essa troca.

 ![Diagrama de arquitetura de controle de código-fonte](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagrama de arquitetura mostrando interação entre VS e plug-in de controle de origem

 Como mostrado no diagrama [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de arquitetura, o shell, rotulado como shell VS no diagrama, hospeda os projetos de trabalho do usuário e componentes associados, como os editores e o Solution Explorer. O pacote do adaptador de controle de origem lida com a interação entre o IDE e o plug-in de controle de origem. O Pacote adaptador de controle de origem fornece sua própria ui de controle de origem. É com a ui de alto nível que o usuário interage para iniciar e definir o escopo de uma operação de controle de origem.

 O plug-in de controle de origem pode ter sua própria ui, que pode consistir de duas partes como mostrado na figura. A caixa rotulada como "UI do fornecedor" representa elementos de interface de usuário personalizados que você, como um criador de plug-in de controle de origem, fornece. Estes são exibidos diretamente pelo plug-in de controle de origem quando o usuário invoca uma operação avançada de controle de origem. A caixa rotulada "Helper UI" é um conjunto de recursos de iu plug-in de controle de fonte que são indiretamente invocados através do IDE. O plug-in de controle de origem passa mensagens relacionadas à UI para o IDE através de funções especiais de retorno de chamada fornecidas pelo IDE. A iU auxiliar facilita uma integração mais perfeita com o IDE (muitas vezes através do uso de um botão **Avançado)** e, portanto, proporciona uma experiência de usuário final mais unificada.

 Um plug-in de controle de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] origem não pode fazer alterações no shell e, consequentemente, no Pacote adaptador de controle de fonte ou na ui de controle de origem fornecida pelo IDE. Ele deve fazer o máximo uso da flexibilidade oferecida através da implementação das várias funções de API plug-in de controle de fonte que contribuem para uma experiência integrada para o usuário final. A seção de referência da documentação da API plug-in de controle de origem inclui informações para alguns recursos avançados de plug-in de controle de origem. Para explorar esses recursos, o plug-in de controle de origem deve declarar seus recursos avançados ao IDE durante a inicialização, e deve implementar funções avançadas específicas para cada recurso.

## <a name="see-also"></a>Confira também
- [Plug-ins de controle do código-fonte](../../extensibility/source-control-plug-ins.md)
- [Glossário](../../extensibility/source-control-plug-in-glossary.md)
- [Criando um plug-in de controle do código-fonte](../../extensibility/internals/creating-a-source-control-plug-in.md)
