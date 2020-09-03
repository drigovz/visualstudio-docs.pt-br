---
title: '&lt;signature&gt; (JavaScript) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- <signature> JavaScript XML tag
- signature JavaScript XML tag
ms.assetid: 319138e7-cfbe-4b37-9643-2ddb7f9c63d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4c640c28ada16a8a03943fcd1362d4fd521772c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671123"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Agrupa um conjunto de elementos relacionados para uma função ou método para fornecer documentação para funções sobrecarregadas.

## <a name="syntax"></a>Sintaxe

```
<signature externalid="id" externalFile="filename"
    helpKeyword="keyword" locid="descriptionID">
</signature>
```

#### <a name="parameters"></a>Parâmetros
 `externalid` Opcional. Se o `format` atributo do [\<loc>](../ide/loc-javascript.md) elemento for `vsdoc` , esse atributo ESPECIFICArá a ID de membro usada para localizar o código XML associado à assinatura. Ao contrário do `locid` atributo, esse atributo especifica que todos os elementos no membro com essa ID devem ser carregados. Todas as informações de descrição associadas presentes no código XML também serão mescladas com os elementos especificados na assinatura. Isso permite que você especifique elementos adicionais, como `<capability>` , no arquivo sidecar sem especificá-los no arquivo de origem. `externalid` é um atributo opcional.

 `externalFile` Opcional. Especifica o nome do arquivo no qual localizar o `externalid` . Esse atributo será ignorado se nenhum `externalid` estiver presente. Esse é um atributo opcional. O valor padrão é o nome do arquivo atual, mas com uma extensão de arquivo. xml em vez de. js. Por padrão, as regras de pesquisa de recursos gerenciados para localização são usadas para localizar o arquivo.

 `helpKeyword` Opcional. A palavra-chave para a ajuda F1.

 `locid` Opcional. O identificador para informações de localização sobre o campo. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo de identificador depende do formato especificado na [\<loc>](../ide/loc-javascript.md) marca.

## <a name="remarks"></a>Comentários
 Use um `<signature>` elemento para cada descrição de função sobrecarregada no arquivo. js ou use um `<signature>` elemento para cada ID de membro externo especificado.

 O `<signature>` elemento deve ser colocado no corpo da função antes de qualquer instrução. Ao usar [\<summary>](../ide/summary-javascript.md) [\<param>](../ide/param-javascript.md) elementos, ou [\<returns>](../ide/returns-javascript.md) com o `<signature>` elemento, coloque os outros elementos dentro do `<signature>` bloco.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir mostra como usar o elemento `<signature>`.

```javascript
// Use of <signature> with externalid.
// Requires use of the <loc> tag to identify the external functions.
function illuminate(light) {
    /// <signature externalid='M:Windows.Devices.Light.Illuminate()' />
    /// <signature externalid='M:Windows.Devices.Light.Illuminate(System.Int32)'>
    ///   <param name='light' type='Number' />
    /// </signature>
}

// Use of <signature> for overloads implemented in JavaScript.
function add(a, b) {
    /// <signature>
    /// <summary>function summary 1</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 2 – differ by number of params</summary>
    /// <param name="a" type="Number">Only 1 parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 3 – differ by parameter type</summary>
    /// <param name="a" type="Number">Number parameter</param>
    /// <param name="b" type="String">String parameter</param>
    /// <returns type="Number" />
    /// </signature>
    /// <signature>
    /// <summary>function summary 4 – differ by return type</summary>
    /// <param name="a" type="Number">The first number</param>
    /// <param name="b" type="Number">The second number</param>
    /// <returns type="String" />
    /// </signature>

    return a + b;
}
```

## <a name="see-also"></a>Consulte Também
 [Comentários de documentação XML](../ide/xml-documentation-comments-javascript.md)
