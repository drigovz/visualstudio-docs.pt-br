---
title: Visão geral do desenvolvimento de soluções do Office (VSTO)
description: Saiba como desenvolver personalizações para as interfaces de usuário Microsoft Office familiares e ferramentas como os recursos de processamento de texto no Word e os recursos de análise de dados do Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- primary interop assemblies, Office
- Office development in Visual Studio, about developing solutions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 03da1c8052140bbe23ce4d99c12d72baef18898f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891950"
---
# <a name="office-solutions-development-overview-vsto"></a>Visão geral do desenvolvimento de soluções do Office (VSTO)
  Usando Microsoft Office como o front-end para soluções, você pode aproveitar as interfaces de usuário e ferramentas conhecidas do Microsoft Office, como os recursos de processamento de texto do Word, os recursos de análise de dados do Excel e os recursos de gerenciamento de email do Outlook. Você pode desenvolver soluções no Visual Studio para personalizar aplicativos do Office e adicionar os recursos específicos necessários para seus processos de negócios. Por exemplo, você pode transformar o Word em um gerador de contratos que reúne contratos fora de partes pré-existentes que podem se tornar editáveis ou não editáveis. Com o Excel, você pode criar uma planilha de orçamento automatizada personalizada para projetos diferentes. Os usuários também podem colocar as soluções do Office offline, o que torna as soluções complexas mais práticas do que seriam se você utilizasse uma arquitetura baseada na Web.

 Este tópico fornece uma visão geral dos tipos de soluções do Office que você pode criar usando os modelos do Ferramentas do Visual Studio for Office (VSTO) disponíveis nas ferramentas para desenvolvedores do Office no Visual Studio. Para obter informações gerais sobre como desenvolver com o Office, consulte o [Office Developer Center](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Escolher um tipo de projeto do Office
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] fornece os seguintes tipos de modelos de projeto para o desenvolvimento do Office baseado em VSTO:

- **Personalizações em nível de documento** são associadas a um documento específico.

- Os **suplementos do VSTO** são associados ao próprio aplicativo.

  Para decidir qual desses tipos de projeto é melhor para sua solução, pense se você deseja que seu código seja executado somente quando um documento específico estiver aberto ou se você quiser que o código esteja disponível sempre que o aplicativo estiver em execução. Para obter mais informações sobre os modelos de projeto, consulte [visão geral dos modelos do Office Project](../vsto/office-project-templates-overview.md).

  Os tipos de projetos que você pode criar dependem de quais aplicativos do Office você instalou no computador de desenvolvimento. Para obter mais informações, consulte [recursos disponíveis por aplicativo do Office e tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Personalizações no nível de documento
 As personalizações em nível de documento consistem em um assembly associado a um único documento, pasta de trabalho ou modelo no Microsoft Office Word ou Microsoft Office Excel. O assembly é carregado quando o documento associado é aberto. Os recursos nas personalizações que você cria estão disponíveis somente quando o documento associado está aberto. As personalizações não podem fazer alterações em todo o aplicativo, como exibir um novo item de menu ou uma guia da faixa de uma quando qualquer documento está aberto.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclui ferramentas para ajudá-lo a criar personalizações em nível de documento. O documento que você personaliza é hospedado como uma superfície de design no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , que permite que você projete o documento arrastando e soltando controles nele. Muitos outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recursos estão disponíveis em projetos de nível de documento, como controles de Windows Forms, vinculação de dados do tipo "arrastar e soltar" e um depurador integrado.

 Para obter mais informações sobre personalizações, consulte os seguintes tópicos:

- [Introdução à programação de personalizações em nível de documento para o Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Introdução à programação de personalizações em nível de documento para o Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>Suplementos do VSTO
 Os suplementos do VSTO consistem em um assembly associado a um aplicativo Microsoft Office. Normalmente, o suplemento do VSTO é executado quando o aplicativo associado é iniciado, embora os usuários também possam carregar os suplementos do VSTO depois que o aplicativo já estiver em execução. Os recursos nos suplementos do VSTO que você cria estão disponíveis para o próprio aplicativo, independentemente de quais documentos estão abertos.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclui ferramentas para ajudá-lo a criar suplementos do VSTO. Os projetos de suplemento incluem uma classe gerada automaticamente que representa o suplemento do VSTO. Essa classe fornece propriedades e eventos que você pode usar para acessar o modelo de objeto do aplicativo host e executar código quando o suplemento do VSTO é carregado e desligado. Muitos outros [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] recursos estão disponíveis em projetos de suplemento do VSTO, como Windows Forms e um depurador integrado.

 Para obter mais informações sobre os suplementos do VSTO, consulte os seguintes tópicos:

- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)

- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatizar aplicativos do Office usando assemblies de interoperabilidade primários
 Você pode incorporar programaticamente os recursos de um aplicativo do Office em sua solução escrevendo um código que acessa o modelo de objeto do aplicativo. Os modelos de objeto são uma organização de classes que expõem a funcionalidade por meio de várias propriedades e métodos. O modelo de objeto para cada aplicativo do Office é diferente.

 Para usar o modelo de objeto de um aplicativo do Office de uma solução criada usando as ferramentas de desenvolvimento do Office no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , você deve usar o pia (assembly de interoperabilidade primária) para o aplicativo. O PIA permite que o código gerenciado em sua solução interaja com o modelo de objeto baseado em COM do aplicativo do Office.

 Você deve ter os PIAs do Office instalados e registrados no cache de assembly global em seu computador de desenvolvimento para executar a maioria das tarefas de desenvolvimento. Para obter mais informações, consulte [configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Os PIAs do Office não são necessários nos computadores dos usuários finais para executar as soluções do VSTO Office. Para obter mais informações, consulte [design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).

 Para obter mais informações sobre como usar os PIAs nas soluções do Office do VSTO, consulte os seguintes tópicos:

- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)

- [Assemblies de interoperabilidade primária do Office](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Executar soluções do Microsoft VSTO Office nos computadores dos usuários finais
 Ao criar uma solução do VSTO Office, considere como os requisitos de implantação podem afetar suas opções de desenvolvimento.

### <a name="deployment-options"></a>Opções de implantação
 Use o ClickOnce ou Windows Installer para implantar soluções que você cria usando as ferramentas de desenvolvimento do Office no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . A implantação do ClickOnce permite que você crie soluções de autoatualização que podem ser instaladas e executadas com a interação mínima do usuário. Os arquivos de Windows Installer (*. msi*) podem ser facilmente distribuídos para computadores de usuário final ou distribuídos usando o Systems Management Server (SMS). Para obter mais informações sobre a implantação de soluções do VSTO Office, consulte [implantar uma solução do Office](../vsto/deploying-an-office-solution.md).

### <a name="install-prerequisites"></a>Instalar pré-requisitos
 Antes que os usuários finais possam executar uma solução que você cria usando as ferramentas de desenvolvimento do Office no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , seus computadores devem ter determinados pré-requisitos instalados. Se você implantar sua solução usando o ClickOnce ou criando um arquivo de Windows Installer, esses pré-requisitos poderão ser instalados com sua solução. Para obter mais informações, consulte [pré-requisitos da solução do Office para implantação](/previous-versions/bb608617(v=vs.110)) e [como instalar pré-requisitos em computadores de usuários finais para executar soluções do Office](/previous-versions/bb608608(v=vs.110)).

### <a name="security"></a>Segurança
 A segurança para soluções do VSTO Office é imposta por uma série de verificações que o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] faz quando instala e carrega a solução. Essas verificações incluem verificar se o local do manifesto de implantação é confiável ou se o certificado usado para assinar o manifesto de implantação é confiável. Para obter mais informações, consulte [proteger soluções do Office](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Confira também
- [Introdução &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Introdução à programação de personalizações em nível de documento para o Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Introdução à programação de personalizações em nível de documento para o Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Introdução à programação de suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
