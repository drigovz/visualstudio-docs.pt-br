---
title: '&lt;RelatedProducts&gt; elemento (Bootstrapper) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f45b8c07cf03dc83969c3500c80b8ee215e3ad69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898718"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; elemento (bootstrapper)
O `RelatedProducts` elemento define outros produtos que dependem de ou que estão incluídos no produto atual.

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
 O `RelatedProducts` um filho do elemento é o `Product` elemento. Ele não tem atributos.

## <a name="dependsonproduct"></a>DependsOnProduct
 O `DependsOnProduct` elemento significa que o produto atual depende do produto e que o produto deve ser instalado antes do atual. Ele é um filho de `RelatedProducts` elemento. Um `RelatedProducts` elemento pode ter um ou mais `DependsOnProduct` elementos.

 `DependsOnProduct` tem o seguinte atributo.

|Atributo|Descrição|
|---------------|-----------------|
|`Code`|O nome do código do produto incluído, conforme especificado pelo `ProductCode` atributo do `Product` elemento. Para obter mais informações, consulte [ \<produto > elemento](../deployment/product-element-bootstrapper.md).|

## <a name="eitherproducts"></a>EitherProducts
 O `EitherProducts` elemento define zero ou mais `DependsOnProduct` elementos, e não tem atributos. Pelo menos um `DependsOnProduct` neste conjunto deve ser instalado antes do produto atual. Um `RelatedProducts` elemento pode ter zero ou mais `EitherProducts` elementos.

## <a name="includesproduct"></a>IncludesProduct
 O `IncludesProduct` elemento significa que um produto está incluído com a instalação atual e não requer uma instalação separada. Ele é um filho de `RelatedProducts` elemento. Um `RelatedProducts` elemento pode ter um ou mais `IncludesProduct` elementos.

 `IncludesProduct` tem o seguinte atributo.

|Atributo|Descrição|
|---------------|-----------------|
|`Code`|O nome do código do produto incluído, conforme especificado pelo `ProductCode` atributo do `Product` elemento. Para obter mais informações, consulte [ \<produto > elemento](../deployment/product-element-bootstrapper.md).|

## <a name="example"></a>Exemplo
 O exemplo de código a seguir especifica que o Microsoft Installer é instalado com o [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]e, portanto, não precisará de uma instalação separada.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Consulte também
- [\<Produto > elemento](../deployment/product-element-bootstrapper.md)