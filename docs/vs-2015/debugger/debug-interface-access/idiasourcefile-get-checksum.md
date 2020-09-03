---
title: IDiaSourceFile::get_checksum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSourceFile::get_checksum method
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f87f5cdd937c0e172e7b96cf0858423b14686d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190748"
---
# <a name="idiasourcefileget_checksum"></a>IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Recupera os bytes de soma de verificação.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cbData`  
 no Tamanho do buffer de dados, em bytes.  
  
 `pcbData`  
 fora Retorna o número de bytes de soma de verificação. O parâmetro não pode ser `NULL`.  
  
 `data`  
 [entrada, saída] Um buffer que é preenchido com os bytes de soma de verificação. Se esse parâmetro for `NULL` , `pcbData` retorna o número de bytes necessários.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Para determinar o tipo de algoritmo de soma de verificação que foi usado para gerar os bytes de soma de verificação, chame o método [IDiaSourceFile:: get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .  
  
 A soma de verificação normalmente é gerada a partir da imagem do arquivo de origem para que as alterações no arquivo de origem sejam refletidas nas alterações nos bytes de soma de verificação. Se os bytes de soma de verificação não corresponderem a uma soma de verificação gerada a partir da imagem carregada do arquivo, o arquivo deverá ser considerado danificado ou adulterado.  
  
 As somas de verificação típicas nunca têm mais de 32 bytes, mas não pressupõem que seja o tamanho máximo de uma soma de verificação. Defina o `data` parâmetro como `NULL` para obter o número de bytes necessários para recuperar a soma de verificação. Em seguida, aloque um buffer do tamanho apropriado e chame esse método mais uma vez com o novo buffer.  
  
## <a name="see-also"></a>Consulte Também  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)
