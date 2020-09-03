---
title: Determinando qual editor abre um arquivo em um projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c79860f770a6b04a17786cfb281fc3c0e4dffda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196769"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>Determinando qual editor abre um arquivo em um projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando um usuário abre um arquivo em um projeto, o ambiente passa por um processo de sondagem, eventualmente abrindo o editor ou designer apropriado para esse arquivo. O procedimento inicial empregado pelo ambiente é o mesmo para editores padrão e personalizados. O ambiente usa uma variedade de critérios ao sondar qual editor usar para abrir um arquivo e o VSPackage deve coordenar com o ambiente durante esse processo.  
  
 Por exemplo, quando um usuário seleciona o comando **abrir** no menu **arquivo** e escolhe `filename` . rtf (ou qualquer outro arquivo com uma extensão. rtf), o ambiente chama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementação de cada projeto, eventualmente percorrendo todas as instâncias de projeto na solução. Os projetos retornam um conjunto de sinalizadores que identificam declarações em um documento por prioridade. Usando a prioridade mais alta, o ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> método apropriado. Para obter mais informações sobre o processo de sondagem, [adicionando projeto e modelos de item de projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
 O projeto de arquivos diversos declara todos os arquivos que não são reivindicados por outros projetos. Dessa forma, os editores personalizados podem abrir documentos antes que os editores padrão os abram. Se um projeto de arquivos diversos alegar um arquivo, o ambiente chamará o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> método para abrir o arquivo com um editor padrão. O ambiente verifica sua lista interna de editores registrados para um que manipula arquivos. rtf. Essa lista está localizada no registro na seguinte chave:  
  
 [HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio \\ < `version`> \Editors \\ {<`editor factory guid`>} \Extensions]  
  
 O ambiente também verifica os identificadores de classe na chave HKEY_CLASSES_ROOT \CLSID para quaisquer objetos que tenham uma subchave DocObject. Se a extensão de arquivo for encontrada lá, uma versão incorporada do aplicativo, como o Microsoft Word, será criada in-loco no Visual Studio. Esses objetos de documento devem ser arquivos compostos que implementam a <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> interface ou o objeto deve implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interface.  
  
 Se não houver nenhuma fábrica de editor para arquivos. rtf no registro, o ambiente procurará na chave HKEY_CLASSES_ROOT \\ . rtf e abrirá o editor especificado lá. Se a extensão de arquivo não for encontrada em HKEY_CLASSES_ROOT, o ambiente usará o editor de texto principal do Visual Studio para abrir o arquivo se ele for um arquivo de texto.  
  
 Se o editor de texto principal falhar, o que ocorrerá se o arquivo não for um arquivo de texto, o ambiente usará seu editor binário para o arquivo.  
  
 Se o ambiente encontrar um editor para a extensão. rtf em seu registro, ele carregará o VSPackage que implementa essa fábrica de editor. O ambiente chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> método no novo VSPackage. O VSPackage chama o `QueryService` para `SID_SVsRegistorEditor` , usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> método para registrar a fábrica do editor com o ambiente.  
  
 O ambiente agora verifica novamente sua lista interna de editores registrados para encontrar a fábrica de editor recém registrada para arquivos. rtf. O ambiente chama a implementação do <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> método, passando o nome do arquivo e o tipo de exibição para criar.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
