---
title: Determinando qual editor abre um arquivo em um projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7037a3b4bfbae1801e802256af240d017d2789
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708653"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>Determine qual editor abre um arquivo em um projeto
Quando um usuário abre um arquivo em um projeto, o ambiente passa por um processo de votação, eventualmente abrindo o editor ou designer apropriado para esse arquivo. O procedimento inicial empregado pelo ambiente é o mesmo para editores padrão e personalizados. O ambiente usa uma variedade de critérios ao votar qual editor usar para abrir um arquivo e o VSPackage deve coordenar com o ambiente durante esse processo.

 Por exemplo, quando um usuário seleciona o comando **Abrir** no menu **Arquivo** e, em seguida, escolhe *filename.rtf* (ou qualquer outro arquivo com uma extensão *.rtf),* o ambiente chama a <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> implementação para cada projeto, eventualmente passando por todas as instâncias do projeto na solução. Os projetos retornam um conjunto de bandeiras que identificam reivindicações em um documento por prioridade. Usando a mais alta prioridade, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> o ambiente chama o método apropriado. Para obter mais informações sobre o processo de votação, consulte [Adicionar modelos de itens de projeto e projeto](../../extensibility/internals/adding-project-and-project-item-templates.md).

 O projeto Arquivos Diversos reivindica todos os arquivos que não são reclamados por outros projetos. Dessa forma, os editores personalizados podem abrir documentos antes que os editores padrão os abram. Se um projeto Arquivos Diversos reivindicar um arquivo, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ambiente chamará o método para abrir o arquivo com um editor padrão. O ambiente verifica sua lista interna de editores registrados para um que lida com arquivos *.rtf.* Esta lista está localizada no registro na seguinte tecla:

 **HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\\<versão>\Editores\\\<editor de fábrica guiade fábrica>\Extensões**

 O ambiente também verifica os identificadores de classe na tecla **HKEY_CLASSES_ROOT\CLSID** para quaisquer objetos que tenham um Subchave **DocObject**. Se a extensão de arquivo for encontrada lá, uma versão incorporada do aplicativo, como o Microsoft Word, será criada no local no Visual Studio. Esses objetos de documento devem <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage> ser arquivos compostos <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> que implementam a interface, ou o objeto deve implementar a interface.

 Se não houver fábrica de editores para arquivos *.rtf* no registro, então o ambiente olhará na HKEY_CLASSES_ROOT tecla **\\.rtf** e abrirá o editor especificado lá. Se a extensão de arquivo não for encontrada em **HKEY_CLASSES_ROOT,** o ambiente usará o editor de texto principal do Visual Studio para abrir o arquivo, se for um arquivo de texto.

 Se o editor de texto principal falhar, o que ocorre se o arquivo não for um arquivo de texto, o ambiente usará seu editor binário para o arquivo.

 Se o ambiente encontrar um editor para a extensão *.rtf* em seu registro, ele carregará o VSPackage que implementa esta fábrica de editores. O ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> chama o método no novo VSPackage. O VSPackage `QueryService` `SID_SVsRegistorEditor`exige , <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> usando o método para registrar a fábrica do editor com o ambiente.

 O ambiente agora verifica novamente sua lista interna de editores registrados para encontrar a fábrica de editores recém-registrada para arquivos *.rtf.* O ambiente chama sua <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> implementação do método, passando o nome do arquivo e o tipo de exibição para criar.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>
- <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>
