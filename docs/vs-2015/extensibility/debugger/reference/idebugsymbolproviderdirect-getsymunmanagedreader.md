---
title: 'IDebugSymbolProviderDirect:: GetSymUnmanagedReader | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- GetSymUnmanagedReader
- IDebugSymbolProviderDirect::GetSymUnmanagedReader
ms.assetid: 147bacfa-f66c-43e0-8a72-e601058dc57f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 842201b2dc5163abcd957d8e76f9505298e07a6e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153108"
---
# <a name="idebugsymbolproviderdirectgetsymunmanagedreader"></a>IDebugSymbolProviderDirect::GetSymUnmanagedReader
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera um leitor de símbolo para código não gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT GetSymUnmanagedReader (  
   ULONG32    ulAppDomainID,  
   GUID       guidModule,  
   IUnknown** ppSymUnmanagedReader  
);  
```  
  
```csharp  
int GetSymUnmanagedReader (  
   uint       ulAppDomainID,  
   Guid       guidModule,  
   out object ppSymUnmanagedReader  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ulAppDomainID`  
 no Identificador do domínio do aplicativo.  
  
 `guidModule`  
 no Identificador exclusivo do módulo.  
  
 `ppSymUnmanagedReader`  
 fora Retorna um objeto que representa o leitor de símbolo para código não gerenciado.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)
