---
title: Adicionando itens às caixas de diálogo adicionar novos itens | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af7f9e5c792785a23ad1674a50abeb4eb6d3cba9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710210"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Adicionar itens à caixa de diálogo Adicionar novo item
O processo para adicionar itens à caixa de diálogo **Adicionar novo item** começa com as chaves do registro. Como mostrado nas entradas de registro a seguir, a seção **AddItemTemplates** contém o caminho e o nome do diretório em que os itens disponibilizados na caixa de diálogo **Adicionar novo item** são colocados.

> [!NOTE]
> A tabela imediatamente seguinte ao segmento de código contém informações adicionais sobre a entrada do registro.

 Esta seção está localizada em **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 O primeiro GUID é o CLSID para projetos desse tipo; o segundo GUID indica o tipo de projeto registrado para os modelos Adicionar itens:

 **\\{C061DB26-5833-11D2-96F5-0000000000000000} \\Modelos de\\modelos\\de additemDir {ACEF4EB2-57CF-11D2-96F4-0000000000000}\\1**

 **@**= #6

 **ModelosDir** = \\&lt;&gt;\\Visual Studio SDK\\&lt;caminho&gt;\\&lt;de&gt;\\&lt;instalação&gt;\\&lt;VSIntegração SomeFolder SomePackage SomeProject SomeProjectItems&gt;

 **ClassPriority** = dword:00000064

| Nome | Type | Dados (do arquivo *.rgs)* | Descrição |
|------------------|-----------| - | - |
| @ (Padrão) | REG_SZ | #%IDS_ADDITEM_TEMPLATES_ENTRY% | ID de recursos para adicionar modelos **de itens.** |
| Modelos de ValDir | REG_SZ | %TEMPLATE_PATH%\\&lt;Alguns Itens de Projeto&gt; | Caminho dos itens do projeto exibidos na caixa de diálogo para o **assistente Adicionar novo item.** |
| Val SortPriority | REG_DWORD | 100[!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]( ) | Determina a ordem de classificação no nó de árvore dos arquivos exibidos na caixa de diálogo **Adicionar novo item.** |

> [!NOTE]
> Os GUIDS para os tipos de projeto Visual C# e Visual Basic são os seguintes:
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}

 O diretório listado para **TemplatesDir**, que é *%TEMPLATE_PATH%\\&lt;SomeProjectItems&gt;*, é o nó no lado esquerdo da caixa de caixa de diálogo **Adicionar novo item.** Elementos adicionais na árvore são baseados no subdiretório dentro desse diretório raiz. Os arquivos disponíveis para serem adicionados ao projeto são os itens no painel direito da caixa de diálogo **Adicionar novo item.**

 Normalmente, esta pasta conterá os arquivos de modelo para o seu projeto, como um arquivo HTML ou *.cpp* de modelo, e quaisquer arquivos *.vsz* para assistentes de partida. Para controlar como os itens são exibidos, você também pode incluir arquivos *.vsdir* para localizar nomes e ícones de diretórios. A seqüência de string localizada é a legenda que aparece na caixa de diálogo que representa este nó na árvore de caixa de caixa de caixa de diálogo **Adicionar novo item.**

 No entanto, você não precisa ter tudo em um arquivo *.vsdir.* Você pode ter um arquivo *.vsdir* para cada item no diretório. Para obter mais informações, consulte [arquivos Dom (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md) e [arquivos de diretório De modelo (.vsdir) arquivos](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

> [!NOTE]
> Os arquivos *.vsdir* nos diretórios de modelo são opcionais. Se você quiser apenas colocar um elemento de projeto no diretório e exibi-lo na caixa de diálogo **Adicionar novo item,** você pode colocar esse arquivo no diretório de modelos especificado na seção **TemplatesDir.** Em seguida, o arquivo será exibido no painel direito da caixa de diálogo **Adicionar novo item** para esse projeto. No entanto, se você quiser exibir uma legenda localizada para o arquivo ou um ícone, você deve incluir pelo menos um arquivo *.vsdir* no diretório de modelos.

## <a name="group-project-items"></a>Itens do projeto do grupo
 Se você quiser conter grupos de modelos em pastas na árvore caixa de diálogo **Adicionar novo item,** você deve ter subdiretórios sob o diretório de modelo raiz com os itens neles. Quando a caixa de diálogo **Adicionar novo item** é exibida aos usuários, eles também verão as subpastas e poderão selecionar elementos do projeto a partir deles.

 A prioridade de classificação no segmento de código determina onde este diretório de modelo será criado na árvore em relação a outros elementos do nó da árvore. Para a caixa de diálogo **Adicionar novo item,** a prioridade de classificação é tudo o que você deve incluir para que seus itens sejam exibidos no local correto na caixa de diálogo.

 Você também pode <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> implementar a interface para filtrar o que é exibido na caixa de diálogo **Adicionar novo item.** Ao implementar esta interface, você pode configurar um diretório de modelo sustal no disco que contém, por exemplo, 50 arquivos de modelo e assistente. Dessa forma, você pode ter diferentes tipos de projeto com 20 arquivos que pertencem a um tipo de projeto, os outros 30 arquivos que pertencem a outro tipo de projeto, e todos os arquivos disponíveis em um tipo geral de projeto. Desta forma, dependendo de qual modelo de projeto é criado, você pode exibir um conjunto diferente de arquivos de modelo.

 Por exemplo, em um projeto Visual Basic, você pode ter projetos web e projetos de clientes. Os formulários da Web não são itens úteis para adicionar a um projeto cliente, e os formulários do Windows não são itens úteis para adicionar a um projeto de servidor Web. Portanto, você pode criar um diretório de modelo que contém todos os arquivos para ambos os tipos de projeto. Em seguida, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>implementando, você pode ocultar itens que não devem ser exibidos com base no tipo de configurações de projeto ou projeto no projeto.

## <a name="filter-project-items"></a>Filtrar itens do projeto
 `IVsFilterAddProjectItemDlg2`fornece para filtragem de elementos na árvore (painel esquerdo) e arquivos de projeto (painel direito) das seguintes maneiras:

- Pelos nomes localizados (legendas exibidas na caixa de diálogo contida no arquivo `IVsFilterAddProjectItemDlg` *.vsdir)* fornecidos por .

- Pelos nomes reais dos arquivos e pastas no disco (não localizado — sem arquivo *.vsdir)* fornecido por `IVsFilterAddProjectItemDlg`.

- Por categoria, fornecida `IVsFilterAddProjectItemDlg2`por .

  Para filtrar por categoria, forneça uma seqüência de categorias a um item no arquivo *.vsdir,* como *formulário da Web* ou *item Cliente* no Visual Basic. O código da caixa de diálogo recupera a classificação da categoria do arquivo *.vsdir* e passa para você. Em seguida, você pode passar `IVsFilterAddProjectItemDlg2` essas informações para sua implementação de filtrar a caixa de diálogo **Adicionar novo item** por categorias. Você também pode filtrar itens para páginas da Web ou como casos de aplicativo do cliente Win32. Além disso, você [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] pode identificar itens marcados como itens mfc (MFC) ou active template library (ATL). Ao identificar esses itens, o sistema de projetos pode definir suas próprias classificações para que o sistema possa ser filtrado com base em categorias e classificações.

  Se você implementar essa funcionalidade de filtro, não será necessário mapear uma tabela de cada item que deve estar oculto. Você pode simplesmente classificar itens em tipos e colocar as classificações no arquivo *.vsdir* ou arquivos. Em seguida, você pode ocultar qualquer um dos itens que têm uma classificação específica implementando a interface. Desta forma, você pode tornar os itens na caixa de diálogo **Adicionar novo item** dinâmico com base no estado dentro do projeto.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Registre modelos de projetos e itens](../../extensibility/internals/registering-project-and-item-templates.md)
- [CATIDs para objetos que normalmente são usados para estender projetos](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
- [Adicionar modelos de itens de projeto e projeto](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Descrição do diretório de modelo (.vsdir) arquivos](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
- [Arquivo Assistente (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
