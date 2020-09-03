---
title: Utilitário CreateExpInstance | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7d778f0f31a7651412915a898bff9e4bdfe6c55f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196986"
---
# <a name="createexpinstance-utility"></a>Utilitário CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use o utilitário CreateExpInstance para criar, redefinir ou excluir uma instância experimental do Visual Studio. Você pode usar a instância experimental para depurar e testar as extensões do Visual Studio sem alterar o produto subjacente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parâmetros  
 /Create  
 Cria a instância experimental.  
  
 /Reset reiniciar  
 Exclui a instância experimental e, em seguida, cria uma nova.  
  
 /Clean  
 Exclui a instância experimental.  
  
 /VSInstance  
 O nome do diretório que contém a instância base do Visual Studio a ser copiada.  
  
 /RootSuffix  
 O sufixo a ser acrescentado ao nome do diretório de instância experimental.  
  
## <a name="remarks"></a>Comentários  
 Quando estiver trabalhando em uma extensão do Visual Studio, você pode pressionar F5 para abrir a instância experimental padrão e instalar a extensão atual. Se nenhuma instância experimental estiver disponível, o Visual Studio criará uma com as configurações padrão.  
  
 O local padrão da instância experimental depende do número de versão do Visual Studio. Por exemplo, para o Visual Studio 2015, o local é%localappdata%\Microsoft\VisualStudio\14.0Exp\ todos os arquivos no local do diretório são considerados parte dessa instância. Quaisquer instâncias experimentais adicionais não serão carregadas pelo Visual Studio, a menos que o nome do diretório seja alterado para o local padrão.  
  
 O Visual Studio não acessa o registro do sistema quando abre a instância experimental. Isso difere das versões anteriores do Visual Studio, que usavam uma versão experimental do hive do registro.  
  
 O utilitário CreateExpInstance substitui o utilitário VsRegEx.  
  
 O exemplo a seguir redefine a instância experimental padrão do Visual Studio.  
  
 **CreateExpInstance.exe/Reset reiniciar/VSInstance = 14.0/RootSuffix = exp**  
  
## <a name="see-also"></a>Consulte Também  
 [Lançando um produto](../../misc/releasing-a-visual-studio-integration-product.md)
