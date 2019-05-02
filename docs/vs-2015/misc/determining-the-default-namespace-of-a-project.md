---
title: Determinando o Namespace padrão de um projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- custom tools, computing default namespace
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
manager: jillfra
ms.openlocfilehash: 0bc5cba2651f447e36491c641e9b0d05f728e5c7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62822570"
---
# <a name="determining-the-default-namespace-of-a-project"></a>Determinando o Namespace padrão de um projeto
Para [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], se o `CustomToolNamespace` propriedade é definida no arquivo de entrada, em seguida, o valor de `CustomToolNamespace` torna-se o valor do parâmetro de namespace padrão passado para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método. Caso contrário, o `wszDefaultNamespace` parâmetro passado para `Generate` é sempre igual ao namespace raiz. Para obter mais informações sobre namespaces, consulte [palavras-chave do Namespace](http://msdn.microsoft.com/library/091a66eb-b10d-4f54-9102-5ac0d4bdb84b).  
  
 [!INCLUDE[csprcs](../includes/csprcs-md.md)] usa namespaces baseados em pastas. Ou seja, o espaço para nome consiste o namespace raiz, além de nomes de qualquer pasta que contém a ferramenta personalizada. Cada nome de pasta é convertido em um identificador válido e períodos separam todos os nomes. Por exemplo, se o arquivo de entrada é FolderA\FolderB\FolderC\MyInput.txt e o namespace raiz é CL9, o namespace padrão computada seria **CL9. FolderA.FolderB.FolderC**.  
  
 Uma exceção a essa regra ocorre quando a cadeia de hierarquia contém uma pasta de referência da Web. Por exemplo, se:  
  
- FolderC eram uma pasta de referência da Web, o namespace seria **CL9. FolderC**.  
  
- PastaB eram uma pasta de referência da Web, o namespace seria **CL9. FolderB.FolderC**.  
  
  Ou seja, o namespace usa o seguinte formato:  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## <a name="see-also"></a>Consulte também  
 [Implementando geradores de arquivo único](../extensibility/internals/implementing-single-file-generators.md)   
 [Registrar geradores de arquivo único](../extensibility/internals/registering-single-file-generators.md)   
 [Expor tipos aos designers visuais](../extensibility/internals/exposing-types-to-visual-designers.md)