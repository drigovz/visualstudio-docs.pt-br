---
title: Símbolos e marcações de símbolos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [DIA SDK]
ms.assetid: 2ee3a262-cda6-48bf-b799-a37edde6c8b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23214e9a0af3ca506677e5f67b4460fa6d9d8414
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54968993"
---
# <a name="symbols-and-symbol-tags"></a>Símbolos e marcações de símbolos
Informações de depuração sobre um programa compilado são armazenadas no arquivo de banco de dados (. PDB) de programa como símbolos que podem ser acessados usando as APIs do SDK de acesso de Interface de depuração (DIA). Todos os símbolos têm uma [idiasymbol:: Get_symtag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) e uma [idiasymbol:: Get_symindexid](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md) propriedade. O `symTag` propriedade indica o tipo de símbolo, conforme definido pelo [enumeração SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) enumeração. O `symIndexId` propriedade é um `DWORD` valor que contém o identificador exclusivo para cada instância de um símbolo.  
  
 Símbolos também têm propriedades que podem especificar informações adicionais sobre o símbolo, bem como referências a outros símbolos, geralmente um [idiasymbol:: Get_lexicalparent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md) ou [idiasymbol:: Get_classparent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md). Quando você consulta uma propriedade que contém uma referência, a referência é retornada como um [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) objeto. Essas propriedades são sempre emparelhadas com outra propriedade com o mesmo nome, mas o sufixo com "Id", por exemplo, [idiasymbol:: Get_lexicalparentid](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md) e [idiasymbol:: Get_classparentid](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md). As tabelas no [locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md), [hierarquia Lexical de tipos de símbolo](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md), e [hierarquia de classe de tipos de símbolo](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md) descrever as propriedades para cada um dos diferentes tipos de símbolos. Essas propriedades podem ter informações relevantes sobre ou referências a outros símbolos. Porque o `*Id` propriedades são identificadores de ordinal simplesmente numéricos de suas propriedades relacionadas, eles são omitidos de discussões ainda mais. Eles são chamados somente quando for necessário para fins de esclarecimento de parâmetro.  
  
 Ao tentar acessar a propriedade, se nenhum erro ocorrer e a propriedade de símbolo foi atribuída um valor, a propriedade "get" retorno do método `S_OK`. Um valor de retorno `S_FALSE` indica que a propriedade não é válida para o símbolo atual.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Locais de símbolos](../../debugger/debug-interface-access/symbol-locations.md)  
 Descreve os diferentes tipos de locais de que um símbolo pode ter.  
  
 [Hierarquia lexical de tipos de símbolo](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)  
 Descreve os tipos de símbolo que formam hierarquias lexicais como arquivos, módulos e funções.  
  
 [Hierarquia de classes de tipos de símbolo](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)  
 Descreve os tipos de símbolo que correspondem aos elementos de linguagem diferentes, como classes, matrizes e a função retornam tipos.  
  
## <a name="see-also"></a>Consulte também  
 [SDK de Acesso à Interface de Depuração](../../debugger/debug-interface-access/debug-interface-access-sdk.md)