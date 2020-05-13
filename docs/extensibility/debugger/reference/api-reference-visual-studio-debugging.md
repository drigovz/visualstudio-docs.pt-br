---
title: Referência em API (Visual Studio Debugging) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], API reference
ms.assetid: e4e429da-3667-41f7-9158-a8207d13e91a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a2df6d82099a927664620e19096107f283afada
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738181"
---
# <a name="api-reference-visual-studio-debugging"></a>Referência de API (depuração no Visual Studio)
A seção de referência inclui uma visão geral conceitual da API, um guia que mostra a sintaxe e o uso de todos os elementos da API, e uma variedade de exemplos de código. Todas as referências são listadas alfabeticamente por categoria.

 A tabela a `HRESULT` seguir mostra os valores comuns retornados por métodos.

|Nome|Descrição|Valor|
|----------|-----------------|-----------|
|S_OK|Sucesso.|0x00000000|
|E_UNEXPECTED|Falha inesperada.|0x8000FFFF|
|E_NOTIMPL|Não implementado.|0x80004001|
|E_OUTOFMEMORY|Não há memória suficiente para completar a operação.|0x8007000E|
|E_INVALIDARG|Um ou mais argumentos são inválidos.|0x80070057|
|E_NOINTERFACE|Nenhuma interface suportada.|0x80004002|
|E_POINTER|Ponteiro inválido.|0x80004003|
|E_HANDLE|Alça inválida.|0x80070006|
|E_ABORT|Operação anulada.|0x80004004|
|E_FAIL|Falha inesperada.|0x80004005|
|E_ACCESSDENIED|Acesso geral negado erro.|0x80070005|

> [!NOTE]
> Quando [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] um método de `S_OK`depuração retorna, presume-se que todos os ponteiros de parâmetro saem `S_OK` válidos, ou seja, nenhuma validação é realizada em ponteiros de parâmetros quando é retornado.
>
> [!NOTE]
> Parâmetros `NULL` inválidos ou [fora] podem causar a falha do IDE.

## <a name="see-also"></a>Confira também
- [Interfaces](../../../extensibility/debugger/reference/interfaces-visual-studio-debugging.md)
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
- [Extensibilidade do depurador do Visual Studio](../../../extensibility/debugger/visual-studio-debugger-extensibility.md)
