---
title: CreateExpInstance Utilitário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709236"
---
# <a name="createexpinstance-utility"></a>Utilitário CreateExpInstance
Use o utilitário **CreateExpInstance** para criar, redefinir ou excluir uma instância experimental do Visual Studio. Você pode usar a instância experimental para depurar e testar extensões do Visual Studio sem alterar o produto subjacente.

## <a name="syntax"></a>Sintaxe

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>parâmetros
 **/Criar** Cria a instância experimental.

 **/Reset** Exclui a instância experimental e, em seguida, cria uma nova.

 **/Limpo** Exclui a instância experimental.

 **/VSInstance** O nome do diretório que contém a instância base do Visual Studio para copiar.

 **/RootSuffix** O sufixo para anexar ao nome do diretório de instância experimental.

## <a name="remarks"></a>Comentários
 Quando você estiver trabalhando em uma extensão do Visual Studio, você pode pressionar F5 para abrir a instância experimental padrão e instalar a extensão atual. Se nenhuma instância experimental estiver disponível, o Visual Studio criará uma que tenha as configurações padrão.

 A localização padrão da instância experimental depende do número da versão do Visual Studio. Por exemplo, para o Visual Studio 2015, a localização é *%localappdata%\Microsoft\VisualStudio\14.0Exp\\*. Todos os arquivos no local do diretório são considerados parte dessa instância. Quaisquer instâncias experimentais adicionais não serão carregadas pelo Visual Studio, a menos que o nome do diretório seja alterado para o local padrão.

 O Visual Studio não acessa o registro do sistema quando abre a instância experimental. Isso difere das versões anteriores do Visual Studio, que usou uma versão experimental da colmeia de registro.

 O utilitário **CreateExpInstance** substitui o utilitário **VsRegEx.**

 O exemplo a seguir redefine a instância experimental padrão do Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Confira também
- [VSPackages](../../extensibility/internals/vspackages.md)
