---
title: IDiaDataSource::openSession | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::openSession method
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bec5507d15374e6e88afd4567d4b0fec9ca6cb7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198597"
---
# <a name="idiadatasourceopensession"></a>IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre uma sessão para consultar símbolos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 ppSession  
 fora Retorna um objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) que representa a sessão aberta.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores de retorno para esse método.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|E_UNEXPECTED|O objeto [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) não foi inicializado anteriormente com uma fonte de símbolos.|  
|E_INVALIDARG|Parâmetro `ppSession` inválido.|  
|E_OUTOFMEMORY|Memória insuficiente para abrir a sessão.|  
  
## <a name="remarks"></a>Comentários  
 Esse método abre um objeto [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para uma fonte de dados.  
  
 `IDiaSession` objetos implementam consultas na fonte de dados. Uma sessão gerencia um espaço de endereço para cada conjunto de símbolos de depuração. Se o arquivo. exe ou. dll descrito pelos símbolos de fonte de dados estiver ativo em vários intervalos de endereços (por exemplo, porque vários processos foram carregados), uma sessão para cada intervalo de endereços deverá ser usada.  
  
## <a name="example"></a>Exemplo  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Sobre](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Consultando o arquivo .Pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
