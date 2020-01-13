---
title: Adicionando extensões às definições de DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5fab56a7738ed7b52760cf20a5bfcc8542ee5a23
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919055"
---
# <a name="adding-extensions-to-dsl-definitions"></a>Adicionando extensões a definições de DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A extensão de definição de DSL permite que você crie um pacote de extensões para uma DSL (linguagem específica de domínio). A extensão de DSL, que está contida em uma extensão de integração do Visual Studio (VSIX), pode ser instalada no computador de um usuário da mesma maneira que uma DSL. Os recursos adicionais podem ser habilitados e desabilitados dinamicamente em tempo de execução. As DSLs não precisam ser explicitamente projetadas para extensão, e as extensões podem ser projetadas mais tarde ou por terceiros sem alterar a DSL estendida.

 Os recursos adicionais podem incluir o seguinte:

- Propriedades para elementos de modelo e apresentação

- Decoradores para formas e conectores

- Classes, relações, formas e conectores

- Restrições de validação

- Itens e guias da caixa de ferramentas

  Um usuário de um DSL estendido pode criar e salvar um modelo que contém instâncias dos recursos adicionais, e eles podem ser lidos por outros usuários que instalaram a extensão apropriada. Os usuários que não instalaram a extensão não podem usar os recursos adicionais, mas eles podem atualizar e salvar um modelo sem perder os recursos adicionais.

  Para obter um exemplo de código e mais informações sobre esse recurso, consulte o site Visual [Studio Visualization and Modeling SDK](https://www.microsoft.com/en-us/download/details.aspx?id=48148) .

## <a name="see-also"></a>Veja também
 [SDK de visualização e modelagem do Visual Studio](https://www.microsoft.com/en-us/download/details.aspx?id=48148)
