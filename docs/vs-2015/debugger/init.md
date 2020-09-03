---
title: Init | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea9f8a24d342668b3574c3798a32c58c124aca7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185854"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Prepara o componente no aplicativo do diagnóstico de gráficos para capturar e gravar ativamente informações de gráficos em um arquivo de log de gráficos.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `vsgLogGetter`  
 Uma entidade que possa ser chamada, como uma função, um ponteiro de função, lambda ou um objeto de função — que usa como parâmetros o comprimento de um buffer composto `wchar_t` e um ponteiro para esse buffer, e retorna `void` . Quando invocado, a entidade callable determina o nome do arquivo que será usado para registrar informações gráficas e grava-o no buffer especificado antes de retornar.  
  
## <a name="remarks"></a>Comentários  
 A `Init` função é chamada automaticamente quando uma instância da `VsgDbg` classe é construída especificando o `bDefaultInit` parâmetro de seu construtor como `true` ; caso contrário, `Init` deve ser chamado explicitamente antes que você possa capturar e registrar informações de gráficos ativamente.  
  
 Você pode finalizar e fechar o arquivo de log de gráficos ativo chamando e `UnInit` , em seguida, capturar e registrar mais informações sobre gráficos em um novo arquivo de log de gráficos chamando `Init` novamente. Você pode repetir isso quantas vezes desejar para criar vários arquivos de log de gráficos independentes usando a mesma `VsgDbg` instância.  
  
## <a name="see-also"></a>Consulte Também  
 [UnInit](../debugger/init.md)
