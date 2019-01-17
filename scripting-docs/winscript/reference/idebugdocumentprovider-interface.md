---
title: Interface IDebugDocumentProvider | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345208"
---
# <a name="idebugdocumentprovider-interface"></a>Interface IDebugDocumentProvider
Fornece os meios para instanciar um documento sob demanda.  
  
## <a name="remarks"></a>Comentários  
 Isso significa indireta para instanciar um documento:  
  
- Permite que o documento a ser carregado quando for necessário.  
  
- Permite que o objeto de documento a ser contido dentro do IDE do depurador.  
  
- Permite que várias maneiras de acessar o mesmo objeto de documento.  
  
  Isso efetivamente separa o documento de seu provedor e permite que o provedor transportar informações de contexto de tempo de execução adicionais.  
  
  Além dos métodos herdados de `IDebugDocumentInfo`, o `IDebugDocumentProvider` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Faz com que o documento a ser instanciado se ele ainda não existir.|