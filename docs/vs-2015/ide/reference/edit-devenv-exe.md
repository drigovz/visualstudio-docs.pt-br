---
title: -Edit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /edit switch
- /Edit Devenv swtich
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c81f59f2dadf535af4e9a76949a29fd1355c33f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657753"
---
# <a name="edit-devenvexe"></a>/Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Abre o arquivo especificado em uma instância existente do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="syntax"></a>Sintaxe

```
Devenv /edit [file1[ file2]]
```

## <a name="arguments"></a>Argumentos
 `file1` Opcional. O arquivo a ser aberto em uma instância existente do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Se nenhuma instância do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] existir, uma nova instância será criada com um layout de janela simplificado, e o `file1` será aberto na nova instância.

 `file2` Opcional. Um ou mais arquivos adicionais a serem abertos na instância existente do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

## <a name="remarks"></a>Comentários
 Se nenhum arquivo for especificado e se houver uma instância existente do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], a instância existente do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] receberá o foco. Se nenhum arquivo for especificado e se não houver nenhuma instância existente do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], uma nova instância do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] será criada com um layout de janela simplificado.

 Se a instância existente do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] estiver em um estado modal, por exemplo, se a [caixa de diálogo Opções](../../ide/reference/options-dialog-box-visual-studio.md) estiver aberta, o arquivo será aberto na instância existente quando [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] sair do estado modal.

## <a name="example"></a>Exemplo
 Esse exemplo abre o arquivo `MyFile.cs` em uma instância existente do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ou abre o arquivo em uma nova instância da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] se ainda não existir nenhuma.

```
devenv /edit MyFile.cs
```

## <a name="see-also"></a>Consulte Também
 [Opções de linha de comando do desenvolvedor](../../ide/reference/devenv-command-line-switches.md)
