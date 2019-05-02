---
title: IDiaAddressMap::put_imageAlign | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaAddressMap::put_imageAlign method
ms.assetid: f9ce875d-c263-43e5-a534-f34c37f9866f
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e0fa57c38c8451bde84d96ab32bc7980c5e2d8b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442213"
---
# <a name="idiaaddressmapputimagealign"></a>IDiaAddressMap::put_imageAlign
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Define o alinhamento da imagem.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
HRESULT put_imageAlign (   
   DWORD NewVal  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 NewVal  
 [in] O novo valor de alinhamento de imagem para o executável.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.  
  
## <a name="remarks"></a>Comentários  
 Imagens (executáveis carregado) são alinhadas a limites de memória especificado. Esse alinhamento pode ser afetado pela arquitetura de sistema atual e pelas opções de tempo de compilação e link. Alinhamento da imagem é sempre em limites de bytes. Os seguintes valores de alinhamento da imagem são válidos: limites de 1, 2, 4, 8, 16, 32 e 64 bytes.  
  
 O alinhamento da imagem atual pode ser recuperado com uma chamada para o [idiaaddressmap:: Get_imagealign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md) método.  
  
> [!NOTE]
> A imagem já está carregada no momento em que esse método pode ser chamado. O `put_imageAlign` método normalmente é usado quando a imagem foi movida ou alterada e um novo alinhamento é necessário.  
  
## <a name="see-also"></a>Consulte também  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaAddressMap::get_imageAlign](../../debugger/debug-interface-access/idiaaddressmap-get-imagealign.md)
