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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02a4c36f3969ca0f9ef61e817afb82eb8247f041
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68203480"
---
# <a name="ltsignaturegt-javascript"></a>&lt;signature&gt; (JavaScript)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Agrupa um conjunto de elementos relacionados para uma função ou um método para fornecer a documentação para funções sobrecarregadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<signature externalid="id" externalFile="filename"  
    helpKeyword="keyword" locid="descriptionID">  
</signature>   
```  
  
#### <a name="parameters"></a>Parâmetros  
 `externalid`  
 Opcional. Se o `format` de atributo para o [ \<loc >](../ide/loc-javascript.md) elemento é `vsdoc`, este atributo especifica o ID usada para localizar o código XML que está associada com a assinatura de membro. Ao contrário de `locid` atributo, este atributo especifica de que todos os elementos no membro que tem essa ID devem ser carregados. Informações de descrição associada presentes no código XML também serão mescladas com os elementos especificados na assinatura. Isso permite que você especifique os elementos adicionais, tais como `<capability>`, no arquivo de sidecar sem especificá-los no arquivo de origem. `externalid` é um atributo opcional.  
  
 `externalFile`  
 Opcional. Especifica o nome do arquivo no qual encontrar o `externalid`. Esse atributo é ignorado se nenhum `externalid` está presente. Este é um atributo opcional. O valor padrão é o nome do arquivo atual, mas com uma extensão de arquivo de. XML, em vez de. js. Por padrão, as regras de pesquisa de recurso gerenciado para a localização são usadas para localizar o arquivo.  
  
 `helpKeyword`  
 Opcional. A palavra-chave para a ajuda F1.  
  
 `locid`  
 Opcional. O identificador para obter informações sobre o campo de localização. O identificador é uma ID de membro ou ele corresponde ao valor do atributo `name` em um pacote de mensagens definido pelos metadados OpenAjax. O tipo do identificador depende do formato especificado na marca [\<loc>](../ide/loc-javascript.md).  
  
## <a name="remarks"></a>Comentários  
 Use um `<signature>` sobrecarregado de elemento para cada descrição de função no arquivo. js ou use um `<signature>` elemento para cada ID de membro externo especificado.  
  
 O `<signature>` elemento deve ser colocado no corpo da função antes que as instruções. Ao usar [ \<resumo >](../ide/summary-javascript.md), [ \<param >](../ide/param-javascript.md), ou [ \<retorna >](../ide/returns-javascript.md) elementos com o `<signature>` elemento, colocar os outros elementos dentro de `<signature>` bloco.  
  
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
  
## <a name="see-also"></a>Veja também  
 [Comentários da documentação XML](../ide/xml-documentation-comments-javascript.md)
