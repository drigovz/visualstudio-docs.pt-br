---
title: IDebugModule3::GetSymbolInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726894"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera uma lista de caminhos que são pesquisados por símbolos, bem como os resultados da pesquisa de cada caminho.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>parâmetros
`dwFields`\
[em] Uma combinação de [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) bandeiras da enumeração `pInfo` SYMBOL_SEARCH_INFO_FIELDS especificando quais campos devem ser preenchidos.

`pInfo`\
[fora] Uma [estrutura MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) cujos membros devem ser preenchidos com as informações especificadas. Se este é um valor `E_INVALIDARG`nulo, este método retorna .

## <a name="return-value"></a>Valor retornado
Se o método for `S_OK`bem sucedido, ele retorna; caso contrário, ele retorna um código de erro.

> [!NOTE]
> A corda devolvida (na `MODULE_SYMBOL_SEARCH_INFO` estrutura) pode `S_OK` estar vazia mesmo se for devolvida. Neste caso, não havia informações de busca para retornar.

## <a name="remarks"></a>Comentários
Se `bstrVerboseSearchInfo` o campo `MODULE_SYMBOL_SEARCH_INFO` da estrutura não estiver vazio, ele contém uma lista de caminhos pesquisados e os resultados dessa pesquisa. A lista é formatada com um caminho, seguido de uma elipse ("..."), seguida pelo resultado. Se houver mais de um par de resultados de caminho, cada par será separado por um par "\r\n" (carriage-return/linefeed). O padrão é assim:

\<caminho>... \<resultado>\r\n\<caminho>... \<resultado>\r\n\<caminho>... \<> de resultados

Observe que a última entrada não tem uma seqüência \r\n.

## <a name="example"></a>Exemplo
Neste exemplo, este método retorna três caminhos com três resultados de pesquisa diferentes. Cada linha é encerrada com um par de transporte-retorno/alimentação de linha. A saída de exemplo apenas imprime os resultados da pesquisa como uma única seqüência.

> [!NOTE]
> Um resultado de status é tudo imediatamente após o "..." até o fim da linha.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:\symbols\user32.pdb... Arquivo não encontrado.** 
 **c:\winnt\symbols\user32.pdb... A versão não bate.** 
 ** \\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Símbolos carregados.**

## <a name="see-also"></a>Confira também

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
