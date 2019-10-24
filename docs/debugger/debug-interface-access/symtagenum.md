---
title: SymTagEnum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- SymTagEnum enumeration
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 806fe878468baa06b52a15879ceaff1b376461e9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738514"
---
# <a name="symtagenum"></a>SymTagEnum
Especifica o tipo de símbolo.

## <a name="syntax"></a>Sintaxe

```C++
enum SymTagEnum {
    SymTagNull,
    SymTagExe,
    SymTagCompiland,
    SymTagCompilandDetails,
    SymTagCompilandEnv,
    SymTagFunction,
    SymTagBlock,
    SymTagData,
    SymTagAnnotation,
    SymTagLabel,
    SymTagPublicSymbol,
    SymTagUDT,
    SymTagEnum,
    SymTagFunctionType,
    SymTagPointerType,
    SymTagArrayType,
    SymTagBaseType,
    SymTagTypedef,
    SymTagBaseClass,
    SymTagFriend,
    SymTagFunctionArgType,
    SymTagFuncDebugStart,
    SymTagFuncDebugEnd,
    SymTagUsingNamespace,
    SymTagVTableShape,
    SymTagVTable,
    SymTagCustom,
    SymTagThunk,
    SymTagCustomType,
    SymTagManagedType,
    SymTagDimension,
    SymTagCallSite,
    SymTagInlineSite,
    SymTagBaseInterface,
    SymTagVectorType,
    SymTagMatrixType,
    SymTagHLSLType
};
```

## <a name="elements"></a>Elementos
`SymTagNull` indica que o símbolo não tem nenhum tipo.

`SymTagExe` indica que o símbolo é um arquivo. exe. Há apenas um símbolo de `SymTagExe` por repositório de símbolo. Ele serve como o escopo global e não tem um pai léxico.

`SymTagCompiland` indica o símbolo de compiland para cada componente compiland do repositório de símbolos. Para aplicativos nativos, `SymTagCompiland` símbolos correspondem aos arquivos de objeto vinculados à imagem. Para alguns tipos de imagens MSIL (Microsoft Intermediate Language), há um compiland por classe.

`SymTagCompilandDetails` indica que o símbolo contém atributos estendidos do compiland. A recuperação dessas propriedades pode exigir o carregamento de símbolos compiland.

`SymTagCompilandEnv` indica que o símbolo é uma cadeia de caracteres de ambiente definida para o compiland.

`SymTagFunction` indica que o símbolo é uma função.

`SymTagBlock` indica que o símbolo é um bloco aninhado.

`SymTagData` indica que o símbolo é dado.

`SymTagAnnotation` indica que o símbolo é para uma anotação de código. Os filhos deste símbolo são cadeias de caracteres de dados constantes (`SymTagData`, `LocIsConstant``DataIsConstant`). A maioria dos clientes ignora esse símbolo.

`SymTagLabel` indica que o símbolo é um rótulo.

`SymTagPublicSymbol` indica que o símbolo é um símbolo público. Para aplicativos nativos, esse símbolo é o símbolo externo COFF encontrado durante a vinculação da imagem.

`SymTagUDT` indica que o símbolo é um tipo definido pelo usuário (estrutura, classe ou União).

`SymTagEnum` indica que o símbolo é uma enumeração.

`SymTagFunctionType` indica que o símbolo é um tipo de assinatura de função.

`SymTagPointerType` indica que o símbolo é um tipo de ponteiro.

`SymTagArrayType` indica que o símbolo é um tipo de matriz.

`SymTagBaseType` indica que o símbolo é um tipo base.

`SymTagTypedef` indica que o símbolo é um `typedef`, ou seja, um alias para outro tipo.

`SymTagBaseClass` indica que o símbolo é uma classe base de um tipo definido pelo usuário.

`SymTagFriend` indica que o símbolo é um amigo de um tipo definido pelo usuário.

`SymTagFunctionArgType` indica que o símbolo é um argumento de função.

`SymTagFuncDebugStart` indica que o símbolo é o local final do código de prólogo da função.

`SymTagFuncDebugEnd` indica que o símbolo é o local inicial do código epílogo da função.

`SymTagUsingNamespace` indica que o símbolo é um nome de namespace, ativo no escopo atual.

`SymTagVTableShape` indica que o símbolo é uma descrição de tabela virtual.

`SymTagVTable` indica que o símbolo é um ponteiro de tabela virtual.

`SymTagCustom` indica que o símbolo é um símbolo personalizado e não é interpretado por DIA.

`SymTagThunk` indica que o símbolo é uma conversão usada para compartilhar dados entre 16 e 32 bits de código.

`SymTagCustomType` indica que o símbolo é um símbolo de compilador personalizado.

`SymTagManagedType` indica que o símbolo está em metadados.

`SymTagDimension` indica que o símbolo é uma matriz multidimensional FORTRAN.

`SymTagCallSite` indica que o símbolo representa o local de chamada.

`SymTagInlineSite` indica que o símbolo representa o site embutido.

`SymTagBaseInterface` indica que o símbolo é uma interface base.

`SymTagVectorType` indica que o símbolo é um tipo de vetor.

`SymTagMatrixType` indica que o símbolo é um tipo de matriz.

`SymTagHLSLType` indica que o símbolo é um tipo de linguagem sombreador de alto nível.

## <a name="remarks"></a>Comentários
Todos os símbolos em um arquivo de depuração têm uma marca de identificação que especifica o tipo do símbolo.

Os valores nessa enumeração são retornados por uma chamada para o método [IDiaSymbol:: get_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) .

Os valores nessa enumeração são passados para os seguintes métodos para limitar o escopo da pesquisa a um tipo de símbolo específico:

- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)

- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)

- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)

- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)

- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)

- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)

- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)

- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: cvconst. h

## <a name="see-also"></a>Consulte também
- [Enumerações e estruturas](../../debugger/debug-interface-access/enumerations-and-structures.md)
- [Hierarquia lexical de tipos de símbolo](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)
- [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)
- [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)
- [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)
- [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)
- [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)
- [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
