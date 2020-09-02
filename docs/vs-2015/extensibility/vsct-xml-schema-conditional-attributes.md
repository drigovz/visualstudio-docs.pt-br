---
title: Atributos condicionais de esquema XML VSCT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422143"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>Atributos condicionais do esquema XML do VSCT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Atributos condicionais podem ser aplicados a todas as listas e itens. Os operadores lógicos e as expressões de expansão de símbolo são avaliados como verdadeiro ou falso. Se for true, a lista ou o item associado será incluído na saída resultante.  
  
 As expansões de token podem ser testadas em outras expansões ou constantes de token. A função definida () é usada para testar se um nome específico foi definido, mesmo que ele não tenha nenhum valor.  
  
 Quando um atributo Condition é aplicado a uma lista, a condição é aplicada a todos os elementos filho na lista. Se um elemento filho contiver um atributo Condition, sua condição será combinada com a expressão pai por uma operação AND.  
  
 Os valores 1, ' 1 ' e ' verdadeiro ' são avaliados como verdadeiros, e 0, ' 0 ' e ' falso ' são avaliados como falso.  
  
## <a name="operators"></a>Operadores  
 Os operadores a seguir podem ser usados para avaliar expressões condicionais.  
  
|Operador|Definição|  
|--------------|----------------|  
|(,)|Agrupamento|  
|!|Não lógico|  
|\<, >, \<=, >=, ==, !=|Relacional e igualdade|  
|e|Boolean|  
|ou|Boolean|  
  
## <a name="examples"></a>Exemplos  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
