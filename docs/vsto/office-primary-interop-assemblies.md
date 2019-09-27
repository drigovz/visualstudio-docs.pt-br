---
title: assemblies de Interoperabilidade primária do Office
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies
- assemblies [Office development in Visual Studio], primary interop assemblies
- Office primary interop assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6a709a59e85f65cf2e0caa0551610dd496bedda5
ms.sourcegitcommit: 689ba54ea14257d13031de881f5d4fe937a36f56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71342508"
---
# <a name="office-primary-interop-assemblies"></a>assemblies de Interoperabilidade primária do Office

Para usar os recursos de um aplicativo do Microsoft Office a partir de um projeto do Office, você deve usar o PIA (assembly de interoperabilidade primário ) para o aplicativo. O PIA permite que código gerenciado interaja com modelo de objeto baseado em COM de um aplicativo do Microsoft Office.

[!include[Add-ins note](includes/addinsnote.md)]

Quando você cria um novo projeto do Office, o Visual Studio adiciona referências aos PIAs necessários na compilação do projeto. Em alguns cenários, pode ser necessário adicionar referências a PIAs extras (por exemplo, se você quiser usar um recurso do Microsoft Office Word em um projeto do Microsoft Office Excel).

Este tópico descreve os seguintes aspectos de uso de PIAs do Microsoft Office em projetos do Office:

- [Separar assemblies de interoperabilidade primários para compilar e executar projetos](#separateassemblies)

- [Usar recursos de vários aplicativos Microsoft Office em um único projeto](#usingfeatures)

- [Lista completa de assemblies de interoperabilidade primária para aplicativos Microsoft Office](#pialist)

Para obter mais informações sobre assemblies de interoperabilidade primária, consulte [assemblies de interoperabilidade primária](/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

<a name="separateassemblies"></a>

## <a name="separate-primary-interop-assemblies-to-build-and-run-projects"></a>Separar assemblies de interoperabilidade primários para compilar e executar projetos

O Visual Studio usa diferentes conjuntos de PIAs no computador de desenvolvimento. Esses diferentes conjuntos de assemblies estão nos seguintes locais:

- Uma pasta no diretório arquivos de programas

  Essas cópias de assemblies são usadas ao gravar códigos e compilar projetos. O Visual Studio instala esses assemblies automaticamente.

- O cache de assembly global

  Essas cópias de assemblies são usadas durante algumas tarefas de desenvolvimento, tais como ao executar ou depurar projetos. O Visual Studio não instala nem registra esses assemblies. Você deve fazer isso sozinho.

### <a name="primary-interop-assemblies-in-the-program-files-directory"></a>Assemblies de interoperabilidade primária no diretório arquivos de programas

Quando você instala o Visual Studio, os PIAs são automaticamente instalados em um local no sistema de arquivos, fora do cache de assembly global. Quando você cria um novo projeto, o Visual Studio adiciona automaticamente referências a essas cópias de PIAs ao seu projeto. O Visual Studio usa essas cópias de PIAs, em vez dos assemblies no cache de assembly global, para resolver referências de tipo quando você desenvolve e compila seu projeto.

Essas cópias de PIAs ajudam o Visual Studio a evitar vários problemas de desenvolvimento que podem ocorrer quando diferentes versões de PIAs estão registradas no cache de assembly global.

A partir do Visual Studio 2017, essas cópias dos PIAs são instaladas nos seguintes locais compartilhados no computador de desenvolvimento:

- `%ProgramFiles%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\`

- (ou `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` em sistemas operacionais de 64 bits)

> [!NOTE]
> Para versões mais antigas do Visual Studio, esses PIAs serão instalados no Ferramentas do Visual Studio para a pasta Office\PIA na pasta `%ProgramFiles%` para essa versão do Visual Studio.
> Por exemplo: `%ProgramFiles(x86)%\Microsoft Visual Studio 14.0\Visual Studio Tools for Office\PIA\`

### <a name="primary-interop-assemblies-in-the-global-assembly-cache"></a>Assemblies de interoperabilidade primária no cache de assembly global

Para realizar certas tarefas de desenvolvimento, os PIAs devem ser instalados e registrados no cache de assembly global no computador de desenvolvimento. Normalmente, os PIAs são instalados automaticamente quando você instala o Office no computador de desenvolvimento. Para obter mais informações, consulte [configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

Os PIAs do Office não são necessários em computadores de usuário final para executar soluções do Office. Para obter mais informações, consulte [design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).

<a name="usingfeatures"></a>

## <a name="use-features-of-multiple-microsoft-office-applications-in-a-single-project"></a>Usar recursos de vários aplicativos Microsoft Office em um único projeto

Cada modelo de projeto do Office em Visual Studio é projetado para funcionar com um único aplicativo do Microsoft Office. Para usar recursos em vários aplicativos do Microsoft Office ou usar recursos em um aplicativo ou componente que não tem projeto no Visual Studio, você deve adicionar uma referência aos PIAs necessários.

Na maioria dos casos, você deve adicionar referências aos pias instalados pelo Visual Studio sob o `%ProgramFiles(x86)%\Microsoft Visual Studio\Shared\Visual Studio Tools for Office\PIA\` diretório. Essas versões dos assemblies aparecem na guia **estrutura** da caixa de diálogo **Gerenciador de referências** . Para obter mais informações, confira [Como: Direcione aplicativos do Office por meio de](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)assemblies de interoperabilidade primária.

Se você tiver instalado e registrado os PIAs no cache de assembly global, essas versões dos assemblies aparecerão na guia **com** da caixa de diálogo **Gerenciador de referências** . Você deve evitar adicionar referências a essas versões de assemblies, porque alguns problemas de desenvolvimento podem ocorrer ao usá-las. Por exemplo, se você tiver registrado versões diferentes dos PIAs no cache de assembly global, seu projeto será automaticamente associado à versão do assembly que foi registrado por último — mesmo se você especificar uma versão diferente do assembly no **com** na caixa de diálogo **Gerenciador de referências** .

> [!NOTE]
> Alguns assemblies são adicionados a um projeto automaticamente quando um assembly que lhes faz referência é adicionado. Por exemplo, as referências aos assemblies `Office.dll` e `Microsoft.Vbe.Interop.dll` são adicionadas automaticamente quando você adiciona uma referência aos assemblies do Word, Excel, Outlook, Microsoft Forms ou Graph.

<a name="pialist"></a>

## <a name="primary-interop-assemblies-for-microsoft-office-applications"></a>Assemblies de interoperabilidade primária para aplicativos Microsoft Office

A tabela a seguir lista os assemblies de interoperabilidade primários [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] que [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)]estão disponíveis para [!INCLUDE[Office_16_short](../vsto/includes/office-16-short-md.md)]o e o.

<br/>

|Aplicativo ou componente do Office|Nome do assembly de interoperabilidade primário|
|-------------------------------------|-----------------------------------|
|Biblioteca de Objetos do Microsoft Access 14.0<br /><br /> Biblioteca de Objetos do Microsoft Access 15.0|Microsoft.Office.Interop.Access.dll|
|Biblioteca de Objetos do Mecanismo de Banco de Dados do Microsoft Office 14.0 Access<br /><br /> Biblioteca de Objetos do Mecanismo de Banco de Dados do Microsoft Office 15.0 Access|Microsoft.Office.Interop.Access.Dao.dll|
|Biblioteca de Objetos do Microsoft Excel 14.0<br /><br /> Biblioteca de Objetos do Microsoft Excel 15.0|[Microsoft.Office.Interop.Excel.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.excel?view=excel-pia)|
|Biblioteca de Objetos do Microsoft Graph 14.0 (usado pelo PowerPoint, Access e Word para gráficos)<br /><br /> Biblioteca de Objetos do Microsoft Graph 15.0|Microsoft.Office.Interop.Graph.dll|
|Biblioteca de Tipos do Microsoft InfoPath 2.0 (apenas para InfoPath 2007)|[Microsoft.Office.Interop.InfoPath.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.infopath?view=infopath-form)|
|Assembly de Interoperabilidade do Microsoft InfoPath XML (apenas para InfoPath 2007)|Microsoft.Office.Interop.InfoPath.Xml.dll|
|Biblioteca de Objetos do Microsoft Office 14.0 (funcionalidade compartilhada do Office)<br /><br /> Biblioteca de Objetos do Microsoft Office 15.0 (funcionalidade compartilhada do Office)|office.dll|
|Controle de Exibição do Microsoft Office Outlook (pode ser usado em páginas Web e aplicativos para acessar a sua caixa de entrada)|Microsoft.Office.Interop.OutlookViewCtl.dll|
|Biblioteca de Objetos do Microsoft Outlook 14.0<br /><br /> Biblioteca de Objetos do Microsoft Outlook 15.0|[Microsoft.Office.Interop.Outlook.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.outlook?view=outlook-pia)|
|Biblioteca de Objetos do Microsoft PowerPoint 14.0<br /><br /> Biblioteca de Objetos do Microsoft PowerPoint 15.0|Microsoft.Office.Interop.PowerPoint.dll|
|Biblioteca de Objetos do Microsoft Project 14.0<br /><br /> Biblioteca de Objetos do Microsoft Project 15.0|[Microsoft.Office.Interop.MSProject.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.msproject?view=office-project-server)|
|Biblioteca de Objetos do Microsoft Publisher 14.0<br /><br /> Biblioteca de Objetos do Microsoft Publisher 15.0|Microsoft.Office.Interop.Publisher.dll|
|Biblioteca de Referência de Objetos da Web do Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesigner.dll|
|Biblioteca de Referência de Objetos de Página do Microsoft SharePoint Designer 14.0|Microsoft.Office.Interop.SharePointDesignerPage.dll|
|Microsoft Smart Tags 2,0 tipo biblioteca de tipos **Observação:**  As marcas inteligentes foram preteridas no [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] e [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].|Microsoft.Office.Interop.SmartTag.dll|
|Biblioteca de Tipos do Microsoft Visio 14.0<br /><br /> Biblioteca de Tipos do Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.dll|
|Biblioteca de Tipos Salvar como Web do Microsoft Visio 14.0<br /><br /> Biblioteca de Tipos Salvar como Web do Microsoft Visio 15.0|Microsoft.Office.Interop.Visio.SaveAsWeb.dll|
|Biblioteca de Tipos de Controle de Desenho do Microsoft Visio 14.0<br /><br /> Biblioteca de Tipos de Controle de Desenho do Microsoft Visio 15.0|Microsoft.Office.Interop.VisOcx.dll|
|Biblioteca de Objetos do Microsoft Word 14.0<br /><br /> Biblioteca de Objetos do Microsoft Word 15.0|[Microsoft.Office.Interop.Word.dll](https://docs.microsoft.com/dotnet/api/microsoft.office.interop.word?view=word-pia)|
|Microsoft Visual Basic for Applications Extensibility 5.3|Microsoft.Vbe.Interop.dll|

### <a name="binding-redirect-assemblies"></a>Assemblies de redirecionamento de associação

Quando você instala e registra os PIAs do Office no cache de assembly global (seja com o Office ou instalando o pacote redistribuível para PIAs), os assemblies de redirecionamento de associação também são instalados apenas no cache de assembly global. Esses assemblies ajudam a garantir que a versão correta dos assemblies de interoperabilidade primários seja carregada em tempo de execução.

Por exemplo, quando uma solução que faz referência ao assembly do [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] é executada em um computador que tem a versão [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] do mesmo assembly de interoperabilidade primário, o assembly de redirecionamento de associação instrui o tempo de execução do [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] para carregar a versão do [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] do assembly de interoperabilidade primário.

Para obter mais informações, confira [Como: Habilitar e desabilitar o redirecionamento](/dotnet/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection)de associação automática.

## <a name="see-also"></a>Consulte também

- [Como: Direcionar aplicativos do Office por meio de assemblies de interoperabilidade primária](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Visão geral do modelo de objeto do Excel](../vsto/excel-object-model-overview.md)
- [Soluções do InfoPath](../vsto/infopath-solutions.md)
- [Visão geral do modelo de objeto do Outlook](../vsto/outlook-object-model-overview.md)
- [Soluções do PowerPoint](../vsto/powerpoint-solutions.md)
- [Soluções de projeto](../vsto/project-solutions.md)
- [Visão geral do modelo de objeto do Visio](../vsto/visio-object-model-overview.md)
- [Visão geral do modelo de objeto do Word](../vsto/word-object-model-overview.md)
- [Referência &#40;geral desenvolvimento do Office no Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)
