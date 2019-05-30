---
title: Elemento Icon | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd56391084788729c0f8439728f9afffd59da946
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311247"
---
# <a name="icon-element"></a>Elemento Icon
O atributo guid da marca do ícone é o guid de um bitmap definido. O `id` atributo seleciona o slot na faixa de bitmap. Esse elemento é opcional. Se esse elemento não estiver incluído o valor de **guidOfficeIcon:msotcidNoIcon** será assumida.

## <a name="syntax"></a>Sintaxe

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Atributos e elementos
 As seções a seguir descrevem atributos, elementos filho e elementos pai.

### <a name="attributes"></a>Atributos

|Atributo|Descrição|
|---------------|-----------------|
|GUID|Necessário. O guid de um bitmap definido.|
|id|Necessário. Seleciona o slot na faixa de bitmap.|

### <a name="child-elements"></a>Elementos filho

|Elemento|Descrição|
|-------------|-----------------|
|nenhuma.|nenhuma.|

### <a name="parent-elements"></a>Elementos pai

|Elemento|Descrição|
|-------------|-----------------|
|[Elemento Buttons](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Consulte também
- [Arquivos de tabela (. VSCT) de comando do Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)