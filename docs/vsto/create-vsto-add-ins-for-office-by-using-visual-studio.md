---
title: Criar suplementos do VSTO para o Office usando o Visual Studio
titleSuffix: ''
ms.custom: seodec18
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e64d97b948f38b4c9b5943d5e561aa865d4f765f
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551670"
---
# <a name="create-vsto-add-ins-for-office-by-using-visual-studio"></a>Criar suplementos do VSTO para o Office usando o Visual Studio
  Você pode usar as ferramentas de desenvolvedor de Microsoft Office no Visual Studio para criar .NET Framework aplicativos que estendam o Office. Esses aplicativos também são chamados de *soluções do Office*.

 As ferramentas do desenvolvedor do Office fornecem recursos que ajudam a criar soluções do Office para atender a uma variedade de necessidades comerciais. As ferramentas incluem modelos de projeto para ajudá-lo a criar soluções do Office usando Visual Basic ou Visual C#, além de designers visuais que ajudam a criam interfaces de usuário personalizada para as soluções do Office.

[!include[Add-ins note](includes/addinsnote.md)]

 Para obter as informações mais recentes sobre o desenvolvimento do Office, consulte os seguintes centros de desenvolvimento no MSDN:

- O [portal de desenvolvimento do Office com Visual Studio Developer](http://go.microsoft.com/fwlink/?LinkId=123844) contém links para informações sobre produtos, exemplos de código, vídeos e recursos da Comunidade sobre como usar o Visual Studio para personalizar aplicativos do Office como parte de suas soluções.

- O [Microsoft Office Developer Center](http://go.microsoft.com/fwlink/?LinkId=83467) contém links para artigos técnicos, exemplos de código, downloads, informações da Comunidade, suporte e outras documentações sobre personalizações do Office e OBAs (Office Business Applicationss).

## <a name="in-this-section"></a>Nesta seção
- [Introdução &#40;ao desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)

 Fornece links para informações sobre como configurar um computador de desenvolvimento para criar soluções do Office, como começar a criar soluções do Office e o que há de novo para desenvolvimento do Office no Visual Studio.

- [Atualizar e migrar soluções do Office](../vsto/upgrading-and-migrating-office-solutions.md)

 Fornece links para informações sobre o processo de atualização de projetos criados usando versões anteriores do Visual Studio.

- [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)

 Fornece links para informações sobre como funcionam as soluções do Office, incluindo informações sobre personalizações em nível de documento e suplementos do VSTO.

- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)

 Fornece informações sobre como criar um projeto do Office e configurá-lo no Visual Studio.

- [Desenvolver soluções do Office](../vsto/developing-office-solutions.md)

 Fornece informações sobre como usar o código gerenciado com soluções do Office, incluindo como personalizar a interface de usuário do Office, trabalhar com dados e solucionar problemas.

- [Soluções do Excel](../vsto/excel-solutions.md)

 Fornece informações sobre como automatizar o Excel, criar soluções do Excel e entender os problemas de globalização específicos do Excel.

- [Soluções do InfoPath](../vsto/infopath-solutions.md)

 Fornece informações sobre como criar modelos de formulário e suplementos do VSTO para o InfoPath.

- [Soluções do Outlook](../vsto/outlook-solutions.md)

 Fornece informações sobre como automatizar o Outlook e criar as regiões de formulário e suplementos do VSTO do Outlook.

- [Soluções do PowerPoint](../vsto/powerpoint-solutions.md)

 Fornece informações sobre como automatizar o PowerPoint e criar suplementos do VSTO do PowerPoint.

- [Soluções de projeto](../vsto/project-solutions.md)

 Fornece informações sobre como automatizar Microsoft Office projeto e criar suplementos do VSTO do projeto.

- [Soluções do Visio](../vsto/visio-solutions.md)

 Fornece informações sobre como automatizar o Visio e criar suplementos do VSTO do Visio.

- [Soluções do Word](../vsto/word-solutions.md)

 Fornece informações sobre como automatizar o Word e criar soluções do Word.

- [Criar soluções do Office](../vsto/building-office-solutions.md)

 Fornece informações sobre as diferenças entre a criação de projetos do Office e outros tipos de projetos no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Depurar projetos do Office](../vsto/debugging-office-projects.md)

 Fornece informações sobre as diferenças entre a depuração de projetos do Office e outros tipos de projetos no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- [Proteger soluções do Office](../vsto/securing-office-solutions.md)

 Fornece informações sobre como os recursos de segurança funcionam em soluções do Office.

- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)

 Fornece informações sobre como criar soluções do Office disponíveis para os usuários e os principais problemas a serem considerados ao escolher um método de implantação.

- [Exemplos e orientações de desenvolvimento do Office](../vsto/office-development-samples-and-walkthroughs.md)

 Fornece links para tópicos que fornecem instruções passo a passo para executar tarefas comuns e aplicativos de exemplo.

- [Referência &#40;geral desenvolvimento do Office no Visual Studio&#41;](../vsto/general-reference-office-development-in-visual-studio.md)

 Fornece links para informações detalhadas sobre assemblies de interoperabilidade primária do Office, manifestos, elementos de interface do usuário e mensagens de erro.

- [Desenvolvimento do &#40;Office de referência gerenciada no Visual Studio&#41;](../vsto/managed-reference-office-development-in-visual-studio.md)

 Fornece links para informações sobre namespaces de API e tipos que são usados em projetos do Office destinados a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Para obter a documentação de referência de API sobre os namespaces e tipos que são usados em projetos do Office direcionados para o .NET Framework 3,5, consulte a seção de referência a seguir na documentação do Visual Studio 2008: [2007 referência gerenciada do sistema](http://go.microsoft.com/fwlink/?LinkId=160658).

- [Referência &#40;de API não gerenciada desenvolvimento do Office no Visual Studio&#41;](../vsto/unmanaged-api-reference-office-development-in-visual-studio.md)

 Contém links para informações sobre interfaces COM que você pode usar para executar ações como carregar e descarregar suplementos do VSTO gerenciados em aplicativos do Office.

## <a name="related-sections"></a>Seções relacionadas
- [Desenvolvimento do Office com o portal do desenvolvedor do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=123844) Fornece recursos adicionais, como artigos técnicos, vídeos e Blogs.

- [Central de desenvolvedores do Visual Studio](http://go.microsoft.com/fwlink/?LinkID=99124) Fornece recursos adicionais do Visual Studio, como artigos técnicos, vídeos e Blogs.

- [Portal do desenvolvedor do Office Business Applications](http://go.microsoft.com/fwlink/?LinkId=99125) Fornece informações sobre o Office Business Applications (OBAs) e como criá-los usando a plataforma do Office System.

- [Microsoft Office seção de desenvolvimento da biblioteca MSDN](http://go.microsoft.com/fwlink/?LinkId=149870) A área da biblioteca MSDN, na qual você pode encontrar artigos e documentação de referência sobre o desenvolvimento de soluções para várias versões do Office (não específicas do desenvolvimento do Office usando o Visual Studio).

- [Desenvolvimento de aplicativos no Visual Studio](https://msdn.microsoft.com/97490c1b-a247-41fb-8f2c-bc4c201eff68) Contém links para tópicos que explicam como você pode usar o Visual Studio para projetar, desenvolver, depurar e implantar aplicativos Web, Web Services XML e aplicativos cliente tradicionais.

- [Programação de .NET Framework no Visual Studio](/previous-versions/visualstudio/visual-studio-2010/k1s94fta(v=vs.100)) Discute o desenvolvimento de aplicativos com o .NET Framework em Visual Basic e C#Visual.
