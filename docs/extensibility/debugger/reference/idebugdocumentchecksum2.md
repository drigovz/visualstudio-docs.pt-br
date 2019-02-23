---
title: IDebugDocumentChecksum2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b40129cb8623e6ea68babe2c480da4e4d4198f3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685580"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Representa uma soma de verificação para um documento de depuração e permite passar a soma de verificação entre componentes.

## <a name="syntax"></a>Sintaxe

```
IDebugDocumentChecksum2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 Essa interface pode ser implementada por qualquer componente que expõe o [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interface. No entanto, ele principalmente é implementado por mecanismos de depuração para que a soma de verificação inserida em um arquivo de símbolo (*.pdb) pode ser passada de volta para o IDE e usada ao localizar uma fonte.

## <a name="methods"></a>Métodos
 A tabela a seguir mostra os métodos de `IDebugDocumentChecksum2`.

|Método|Descrição|
|------------|-----------------|
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Recupera o identificador de soma de verificação e o algoritmo de documento dado o número máximo de bytes a serem usados.|

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll