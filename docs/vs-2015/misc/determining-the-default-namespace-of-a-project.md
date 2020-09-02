---
title: Determinando o namespace padrão de um projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 1d58c8986922c30192d6300a623a635b24c34ed5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65705767"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Determinando o namespace padrão de um projeto
Para [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , se a `CustomToolNamespace` propriedade for definida no arquivo de entrada, o valor de `CustomToolNamespace` se tornará o valor do parâmetro de namespace padrão passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método. Caso contrário, o `wszDefaultNamespace` parâmetro passado para `Generate` é sempre igual ao namespace raiz. Para obter mais informações sobre namespaces, consulte [palavras-chave do namespace](https://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] usa namespaces baseados em pasta. Ou seja, o namespace consiste no namespace raiz, além de nomes de qualquer pasta que contenha a ferramenta personalizada. Cada nome de pasta é convertido em um identificador válido e os pontos separam todos os nomes. Por exemplo, se o arquivo de entrada for FolderA\FolderB\FolderC\MyInput.txt e o namespace raiz for CL9, o namespace padrão calculado será **CL9. PastaA. FolderB. FolderC**.  
  
 Uma exceção a essa regra ocorre quando a cadeia de hierarquia contém uma pasta de referência Web. Por exemplo, se:  
  
- FolderC fosse uma pasta de referência da Web, o namespace seria **CL9. FolderC**.  
  
- FolderB fosse uma pasta de referência da Web, o namespace seria **CL9. FolderB. FolderC**.  
  
  Ou seja, o namespace usa o seguinte formato:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Implementando geradores de arquivo único](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrando geradores de arquivo único](../extensibility/internals/registering-single-file-generators.md)   
 [Expondo tipos para designers visuais](../extensibility/internals/exposing-types-to-visual-designers.md)