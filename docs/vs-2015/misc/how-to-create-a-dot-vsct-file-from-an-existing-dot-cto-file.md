---
title: 'Como: criar um. Arquivo vsct de um existente. Arquivo CTO | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .cto file
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
manager: jillfra
ms.openlocfilehash: 83608d768940158dcdab427a557577677e56f7c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62822432"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-cto-file"></a>Como criar um arquivo .Vsct de um arquivo .Cto já existente
Você pode criar um arquivo. vsct baseado em XML de um arquivo binário. CTO existente. Isso permite que você aproveite o novo formato de compilador de tabela de comando. Esse processo funciona mesmo que o arquivo. CTO tenha sido compilado a partir de um arquivo. CTC. Você pode editar e compilar o arquivo. vsct em outro arquivo. CTO.  
  
### <a name="to-create-a-vsct-file-from-a-cto-file"></a>Para criar um arquivo. vsct de um arquivo. CTO  
  
1. Obtenha cópias do arquivo. CTO e seu arquivo. ctsym correspondente.  
  
2. Coloque os arquivos no mesmo diretório que o compilador de vsct.exe.  
  
3. No prompt de comando do Visual Studio, vá para o diretório que contém os arquivos. CTO e. ctsym.  
  
4. Digite **vsct.exe** _ctofilename_**. CTO** _vsctfilename_**. vsct-S**_symfilename_**. ctsym**.  
  
     `ctofilename` é o nome do arquivo. CTO, `vsctfilename` é o nome do arquivo vsct que você deseja criar e `symfilename` é o nome do arquivo. ctsym.  
  
     Esse processo cria um novo arquivo de compilador de tabela de comandos XML. vsct. Você pode editar e compilar o arquivo com vsct.exe, o compilador vsct, como faria com qualquer outro arquivo. vsct.  
  
## <a name="see-also"></a>Consulte Também  
 [Como: criar um. Arquivo vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)