---
title: IDebugComPlusSymbolProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider interface
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 482ea1b2fb2eb7ddad46bd99694e4599e9fd9bbe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733467"
---
# <a name="idebugcomplussymbolprovider"></a>IDebugComPlusSymbolProvider
Representa um provedor de símbolos COM+ com métodos específicos para código gerenciado.

## <a name="syntax"></a>Sintaxe

```
IDebugComPlusSymbolProvider : IDebugSymbolProvider
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Embora não haja separação entre interfaces que sejam úteis a um avaliador de expressão (EE) e aquelas que se destinam a ser usadas por um mecanismo de depuração (DE), os seguintes métodos provavelmente interessarão apenas aos desenvolvedores DE: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFrom, ReplaceSymbols, UnloadSymbols e UpdateSymbols.

## <a name="methods"></a>Métodos
 Além dos métodos na interface [IDebugSymbolProvider,](../../../extensibility/debugger/reference/idebugsymbolprovider.md) esta interface implementa os seguintes métodos:

|Método|Descrição|
|------------|-----------------|
|[AreSymbolsLoaded](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-aresymbolsloaded.md)|Determina se os símbolos de depuração estão carregados para o módulo especificado dado o identificador de domínio do aplicativo.|
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Cria um tipo a partir do tipo primitivo especificado.|
|[GetAddressesInModuleFromPosition](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getaddressesinmodulefromposition.md)|Mapeia uma posição de documento no módulo especificado para uma matriz de endereços de depuração.|
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Recupera informações de tipo sobre a matriz especificada dado seu endereço de depuração.|
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Recupera o nome do conjunto dado o seu módulo e domínio de aplicativo.|
|[GetAttributedClassesForLanguage](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesforlanguage.md)|Recupera as classes com o atributo especificado que são implementados na linguagem de programação dada.|
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|Recupera as classes com o atributo especificado em um determinado módulo.|
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Recupera o ponto de entrada do aplicativo.|
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Recupera o endereço dentro de uma função que representa o deslocamento da linha dado.|
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Recupera o layout das variáveis locais para um conjunto de métodos.|
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Retorna o nome associado ao token especificado dado seu objeto de metadados.|
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|Recupera os símbolos de depuração com o atributo pai dado para o módulo especificado.|
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Recupera o leitor de símbolos para ser usado por código não gerenciado.|
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Recupera-se para um tipo de símbolo dado o seu endereço de depuração.|
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Determina se a função no endereço de depuração especificado é excluída.|
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Determina se a função no endereço de depuração especificado é considerada obsoleta.|
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Determina se o código no endereço de depurador especificado está oculto.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Carrega os símbolos de depuração especificados na memória.|
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Carrega símbolos de depuração dado o fluxo de dados.|
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Substitui os símbolos de depuração atuais pelos do fluxo de dados especificado.|
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Descarrega os símbolos de depuração para o módulo especificado da memória.|
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Atualiza os símbolos de depuração na memória com aqueles do fluxo de dados especificado.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
