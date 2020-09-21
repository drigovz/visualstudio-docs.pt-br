---
title: 'Como: criar um. Arquivo vsct de um existente. Arquivo CTC | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, creating based on a .ctc file
ms.assetid: 700e80a4-c1e1-4178-af53-45e86dd2c08b
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 7b963436e9d968dd5ba3829e97d0fd0c52e49641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838398"
---
# <a name="how-to-create-a-vsct-file-from-an-existing-ctc-file"></a>Como criar um arquivo .Vsct de um arquivo .Ctc existente
Você pode criar um arquivo. vsct baseado em XML de um arquivo de origem. CTC de tabela de comandos existente. Ao fazer isso, você pode aproveitar o novo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] formato de compilador vsct (tabela de comandos com base em XML).  
  
### <a name="to-create-a-vsct-file-from-a-ctc-file"></a>Para criar um arquivo. vsct de um arquivo. CTC  
  
1. Obtenha uma cópia da linguagem Perl.  
  
2. Obtenha uma cópia do script Perl ConvertCTCToVSCT.pl, normalmente localizada na *\<Visual Studio SDK installation path>* pasta \VisualStudioIntegration\Tools\bin.  
  
3. Obtenha uma cópia do arquivo de origem. CTC que você deseja converter.  
  
4. Coloque os arquivos no mesmo diretório.  
  
5. Na [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] janela do prompt de comando, navegue até o diretório.  
  
6. Tipo  
  
    ```  
    perl.exe ConvertCTCtoVSCT.pl PkgCmd.ctc PkgCmd.vsct  
    ```  
  
     em que PkgCmd. CTC é o nome do arquivo. CTC e PkgCmd. vsct é o nome do arquivo. vsct que você deseja criar.  
  
     Isso cria um novo arquivo de origem de tabela de comandos XML. vsct. Você pode compilar o arquivo usando Vsct.exe, o compilador VSCT, como faria com qualquer outro arquivo. vsct.  
  
    > [!NOTE]
    > Você pode melhorar a legibilidade do arquivo. vsct Reformatando os comentários XML.  
  
## <a name="see-also"></a>Consulte Também  
 [Como: criar um. Arquivo vsct](../extensibility/internals/how-to-create-a-dot-vsct-file.md)   
 [Arquivos .Vsct (Visual Studio Command Table)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)