---
title: Classificação, filtragem e agrupamento (XML Schema Explorer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c28842a92ab598ff196e80fc96678c256e4db8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656144"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Classificação, filtragem e agrupamento (XML Schema Explorer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico descreve as opções disponíveis por meio do menu **Opções de classificação, filtragem e agrupamento** na barra de ferramentas do Gerenciador de esquema XML.

## <a name="filter-options"></a>Opções de filtro
 As seguintes opções de filtro estão disponíveis. Por padrão, as opções **Mostrar namespaces** e **Mostrar arquivos de esquema** estão selecionadas.

- **Mostrar namespaces**.

- **Mostrar arquivos de esquema**.

- **Mostrar compositores (sequência/escolha/tudo)**.

## <a name="sorting-options"></a>Opções de classificação
 As seguintes opções de classificação estão disponíveis. O padrão é **classificar por tipo**. O tipo por opções não se aplica a arquivos e para namespaces.

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

## <a name="persisting-sortfilter-options"></a>Gravando o tipo/opções de filtro
 A classificação, filtragem, e opções de agrupamento são salvas no Registro para cada usuário, não importa qual a solução ou arquivos estavam aberta quando as configurações foram alteradas.
