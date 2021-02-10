---
title: '&lt;&gt;Elemento RelatedProducts (Bootstrapper) | Microsoft Docs'
description: O elemento RelatedProducts define outros produtos que dependem ou estão incluídos no produto atual.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a7987306d9f7fc25f9f9b783d5b0966ac5015ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949682"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;&gt;Elemento RelatedProducts (Bootstrapper)
O `RelatedProducts` elemento define outros produtos que dependem ou estão incluídos no produto atual.

## <a name="syntax"></a>Sintaxe

```xml
<RelatedProducts>
    <DependsOnProduct
        Code
    />
    <EitherProducts>
        <DependsOnProduct
            Code
        />
    </EitherProducts>
    <IncludesProduct
        Code
    />
</RelatedProducts>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `RelatedProducts` elemento é um filho do `Product` elemento. Ele não tem atributos.

## <a name="dependsonproduct"></a>DependsOnProduct
 O `DependsOnProduct` elemento significa que o produto atual depende do produto nomeado e que o produto nomeado deve ser instalado antes do atual. É um filho do `RelatedProducts` elemento. Um `RelatedProducts` elemento pode ter um ou mais `DependsOnProduct` elementos.

 `DependsOnProduct` tem o seguinte atributo.

|Atributo|Descrição|
|---------------|-----------------|
|`Code`|O nome do código do produto incluído, conforme especificado pelo `ProductCode` atributo do `Product` elemento. Para obter mais informações, consulte [ \<Product> elemento](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 O `EitherProducts` elemento define zero ou mais `DependsOnProduct` elementos e não tem nenhum atributo. Pelo menos um `DependsOnProduct` nesse conjunto deve ser instalado antes do produto atual. Um `RelatedProducts` elemento pode ter zero ou mais `EitherProducts` elementos.

## <a name="includesproduct"></a>IncludesProduct
 O `IncludesProduct` elemento significa que um produto está incluído na instalação atual e não requer uma instalação separada. É um filho do `RelatedProducts` elemento. Um `RelatedProducts` elemento pode ter um ou mais `IncludesProduct` elementos.

 `IncludesProduct` tem o seguinte atributo.

|Atributo|Descrição|
|---------------|-----------------|
|`Code`|O nome do código do produto incluído, conforme especificado pelo `ProductCode` atributo do `Product` elemento. Para obter mais informações, consulte [ \<Product> elemento](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a>Exemplo
 O exemplo de código a seguir especifica que o Microsoft Installer é instalado com o .NET Framework e, portanto, não precisará de uma instalação separada.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Confira também
- [\<Product> elementos](../deployment/product-element-bootstrapper.md)