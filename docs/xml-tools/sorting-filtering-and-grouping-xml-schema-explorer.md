---
title: Classificação, filtragem e agrupamento no XML Schema Explorer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd288171cd8713e6b403f71a4eee6ba09d3f6ea9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75592510"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Classificação, filtragem e agrupamento (XML Schema Explorer)

Este tópico descreve as opções disponíveis por meio do menu **Opções de classificação, filtragem e agrupamento** na barra de ferramentas do **Gerenciador de esquema XML** .

## <a name="filter-options"></a>Opções de filtro

As seguintes opções de filtro estão disponíveis. Por padrão, as opções **Mostrar namespaces** e **Mostrar arquivos de esquema** estão selecionadas.

- **Mostrar namespaces**.

- **Mostrar arquivos de esquema**.

- **Mostrar compositores (sequência/escolha/tudo)**.

## <a name="sorting-options"></a>Opções de classificação

As seguintes opções de classificação estão disponíveis. O padrão é **classificar por tipo**. As opções **classificar por** não se aplicam a arquivos e namespaces.

- **Classificar por tipo**.

- **Classificar por nome**.

- **Ordem do documento**.

### <a name="sort-by-type"></a>Classificar por Tipo

Quando a opção **classificar por tipo** é selecionada, os nós globais são classificados na seguinte ordem. Nós são classificados em ordem alfabética dentro de cada grupo.

1. `import` Nós.

2. `include` Nós.

3. `redefine` Nós.

4. `attribute` Nós.

5. `attributeGroup` Nós.

6. `complexType` Nós.

7. `simpleType` Nós.

8. `element` Nós.

9. `group` Nós.

### <a name="sort-by-name"></a>Classificar por Nome

Quando a opção **classificar por nome** for selecionada, os nós globais serão classificados na seguinte ordem:

1. `import` Nós (em ordem alfabética de namespaces).

2. `include` Nós (em ordem alfabética de `schemaLocation` atributos).

3. `redefine` Nós (em ordem alfabética de `schemaLocation` atributos).

4. Outros nós globais em ordem alfabética.

### <a name="document-order"></a>Ordem de documento

A opção **ordem de documento** está disponível quando a opção **Mostrar arquivos de esquema** está selecionada. Quando a **ordem do documento** é selecionada, os nós globais são exibidos na ordem em que aparecem no arquivo de esquema.

## <a name="persisting-sortfilter-options"></a>Persistência das opções de classificação/filtro

A classificação, filtragem, e opções de agrupamento são salvas no Registro para cada usuário, não importa qual a solução ou arquivos estavam aberta quando as configurações foram alteradas.
