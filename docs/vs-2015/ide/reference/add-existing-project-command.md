---
title: Comando Adicionar projeto existente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7523db6598a32c76944c22bfdabe56ee288c6b43
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54771076"
---
# <a name="add-existing-project-command"></a>Comando Adicionar Projeto Existente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Adiciona um projeto existente à solução atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Opcional. O caminho completo e nome do projeto, com a extensão, do projeto a adicionar à solução.  
  
 Se o argumento `filename` incluir espaços, ele deverá ficar entre aspas.  
  
 Se nenhum nome de arquivo for especificado, o comando abrirá a caixa de diálogo de arquivo para que o usuário possa escolher um projeto.  
  
## <a name="remarks"></a>Comentários  
 O preenchimento automático tenta localizar o caminho e o nome do arquivo corretos enquanto você digita.  
  
## <a name="example"></a>Exemplo  
 Este exemplo adiciona o projeto [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], TestProject1, à solução atual.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Consulte também  
 [Comandos do Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Janela Comando](../../ide/reference/command-window.md)   
 [Caixa Localizar/Comando](../../ide/find-command-box.md)   
 [Aliases de comando do Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
