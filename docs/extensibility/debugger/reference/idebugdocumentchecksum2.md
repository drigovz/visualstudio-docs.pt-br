---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03cfb29cc54a2f0ab18bce3ec0761cfab62e20df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731904"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Representa um resumo de verificação de um documento de depuração e permite passar a soma de verificação entre os componentes.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface pode ser implementada por qualquer componente que exponha a interface [IDebugDocumentContext2.](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) No entanto, ele é implementado principalmente por mecanismos de depuração para que o resumo de verificação incorporado em um arquivo de símbolo (*.pdb) possa ser passado de volta para o IDE e usado ao encontrar uma fonte.

## <a name="methods"></a>Métodos
 A tabela a seguir `IDebugDocumentChecksum2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera o resumo do documento e o identificador de algoritmo, dado o número máximo de bytes a serem usados.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll
