---
title: Adicionando extensões a definições de DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fa5c02fc28e7ffec4765d94758c838ab149e7ac3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62960479"
---
# <a name="add-extensions-to-dsl-definitions"></a>Adicionar extensões a definições de DSL

Extensão de definição de DSL permite que você crie um pacote de extensões para uma linguagem específica de domínio (DSL). A extensão DSL, que está contida em um Visual Studio Integration VSIX (extensão), pode ser instalada no computador do usuário da mesma maneira como uma DSL. Os recursos adicionais podem ser habilitados e desabilitados em tempo de execução dinamicamente. DSLs não precisam ser explicitamente criado para a extensão e as extensões podem ser projetadas mais tarde, ou por terceiros, sem alterar a DSL estendida.

Extensões DSL podem incluir os seguintes recursos:

- Propriedades de elementos de modelo e apresentação

- Decoradores de formas e conectores

- Classes, relações, formas e conectores

- Restrições de validação

- Guias e itens de caixa de ferramentas

Um usuário de uma DSL estendido pode criar e salvar um modelo que contém as instâncias dos recursos adicionais. O modelo pode ser lido por outros usuários que tenham instalado a extensão apropriada. Os usuários que não tem instalado a extensão não é possível usar os recursos adicionais, mas eles podem atualizar e salvar um modelo sem perder os recursos adicionais.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>Consulte também

- [Postagens de blogs relacionadas](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
