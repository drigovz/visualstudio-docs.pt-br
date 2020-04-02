---
title: Visão geral do desenvolvimento de soluções de escritório (VSTO)
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: abb58d30e33ab5cfe713175b40cd32f593921ae9
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80543943"
---
# <a name="office-solutions-development-overview-vsto"></a>Visão geral do desenvolvimento de soluções de escritório (VSTO)
  Ao usar o Microsoft Office como front-end para soluções, você pode aproveitar as interfaces e ferramentas de usuário do Microsoft Office familiares, como os recursos de processamento de texto no Word, os recursos de análise de dados do Excel e os recursos de gerenciamento de e-mails do Outlook. Você pode desenvolver soluções no Visual Studio para personalizar aplicativos do Office e adicionar os recursos específicos necessários para seus processos de negócios. Por exemplo, você pode transformar o Word em um gerador de contratos que monta contratos a partir de peças pré-existentes que podem ser editáveis ou não editáveis. Com o Excel, você pode criar uma planilha de orçamento automatizada personalizada para diferentes projetos. Seus usuários também podem levar soluções de escritório offline, o que torna as soluções complexas mais práticas do que seriam se você usar uma arquitetura baseada na Web.

 Este tópico fornece uma visão geral dos tipos de soluções do Office que você pode criar usando os modelos visual studio tools for Office (VSTO) disponíveis nas ferramentas de desenvolvedor do Office no Visual Studio. Para obter informações gerais sobre como desenvolver com o Office, consulte o [centro de desenvolvedores do Office](https://developer.microsoft.com/office).

## <a name="choose-an-office-project-type"></a>Escolha um tipo de projeto do Office
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]fornece os seguintes tipos de modelos de projeto para o desenvolvimento do Office baseado em VSTO:

- **Personalizações em nível de documento** estão associadas a um documento específico.

- **Os complementos vsto** estão associados ao próprio aplicativo.

  Para decidir qual desses tipos de projeto é o melhor para sua solução, pense se você quer que seu código seja executado apenas quando um documento específico estiver aberto ou se você deseja que o código esteja disponível sempre que o aplicativo estiver sendo executado. Para obter mais informações sobre os modelos de projeto, consulte [a visão geral dos modelos de projeto do Office](../vsto/office-project-templates-overview.md).

  Os tipos de projetos que você pode criar dependem de quais aplicativos do Office você instalou no computador de desenvolvimento. Para obter mais informações, consulte [Recursos disponíveis pelo aplicativo office e tipo de projeto](../vsto/features-available-by-office-application-and-project-type.md).

### <a name="document-level-customizations"></a>Personalizações no nível de documento
 As personalizações em nível de documento consistem em um conjunto associado a um único documento, pasta de trabalho ou modelo no Microsoft Office Word ou no Microsoft Office Excel. O conjunto é carregado quando o documento associado é aberto. Os recursos nas personalizações que você cria só estão disponíveis quando o documento associado estiver aberto. As personalizações não podem fazer alterações em todo o aplicativo, como exibir um novo item do menu ou uma guia de fita quando qualquer documento estiver aberto.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]inclui ferramentas para ajudá-lo a criar personalizações em nível de documento. O documento que você personaliza está [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]hospedado como uma superfície de design em , o que permite que você projete o documento arrastando e soltando controles nele. Muitos [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] outros recursos estão disponíveis em projetos de nível de documento, como controles do Windows Forms, vinculação de dados de arrastar e soltar e um depurador integrado.

 Para obter mais informações sobre personalizações, consulte os seguintes tópicos:

- [Comece a programar personalizações em nível de documento para excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)

- [Comece a programar personalizações em nível de documento para o Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)

- [Arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md)

### <a name="vsto-add-ins"></a>Complementos vsto
 Os complementos do VSTO consistem em um conjunto associado a um aplicativo do Microsoft Office. Normalmente, o Add-in VSTO é executado quando o aplicativo associado é iniciado, embora os usuários também possam carregar add-ins VSTO depois que o aplicativo já estiver sendo executado. Os recursos em Complementos VSTO que você cria estão disponíveis para o próprio aplicativo, independentemente de quais documentos estão abertos.

 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]inclui ferramentas para ajudá-lo a criar add-ins VSTO. Projetos adicionais incluem uma classe gerada automaticamente que representa o Complemento VSTO. Esta classe fornece propriedades e eventos que você pode usar para acessar o modelo de objeto do aplicativo host e executar código quando o Add-in VSTO é carregado e desligado. Muitos [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] outros recursos estão disponíveis em projetos de complemento VSTO, como o Windows Forms e um depurador integrado.

 Para obter mais informações sobre os complementos do VSTO, consulte os seguintes tópicos:

- [Comece a programar add-ins vsto](../vsto/getting-started-programming-vsto-add-ins.md)

- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)

## <a name="automate-office-applications-by-using-primary-interop-assemblies"></a>Automatize aplicativos do Office usando conjuntos de interop primários
 Você pode incorporar programáticamente os recursos de um aplicativo do Office em sua solução escrevendo código que acessa o modelo de objeto do aplicativo. Os modelos de objeto são um arranjo de classes que expõem a funcionalidade através de várias propriedades e métodos. O modelo de objeto para cada aplicação do Office é diferente.

 Para usar o modelo de objeto de um aplicativo office a [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]partir de uma solução criada usando as ferramentas de desenvolvimento do Office em , você deve usar o conjunto interop primário (PIA) para a aplicação. O PIA permite que o código gerenciado em sua solução interaja com o modelo de objeto baseado em COM do aplicativo Office.

 Você deve ter os PIAs do Office instalados e registrados no cache de montagem global em seu computador de desenvolvimento para executar a maioria das tarefas de desenvolvimento. Para obter mais informações, consulte [Configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md). Os PIAs do Office não são necessários em computadores de usuário final para executar soluções do VSTO Office. Para obter mais informações, consulte [Design e crie soluções do Office](../vsto/designing-and-creating-office-solutions.md).

 Para obter mais informações sobre como usar os PIAs nas soluções do VSTO Office, consulte os seguintes tópicos:

- [Escrever código em soluções do Office](../vsto/writing-code-in-office-solutions.md)

- [Montagens de interop primárias do escritório](../vsto/office-primary-interop-assemblies.md)

## <a name="run-microsoft-vsto-office-solutions-on-end-user-computers"></a>Execute as soluções do Microsoft VSTO Office em computadores de usuário final
 Ao criar uma solução VSTO Office, considere como os requisitos de implantação podem afetar suas escolhas de desenvolvimento.

### <a name="deployment-options"></a>Opções de implantação
 Use o ClickOnce ou o Windows Installer para implantar [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]soluções que você cria usando as ferramentas de desenvolvimento do Office em . A implantação do ClickOnce permite criar soluções de auto-atualização que podem ser instaladas e executadas com o mínimo de interação do usuário. Os arquivos do Windows Installer *(.msi)* podem ser facilmente distribuídos para computadores do usuário final ou distribuídos usando SMS (Systems Management Server). Para obter mais informações sobre a implantação de soluções do VSTO Office, consulte [Implantar uma solução office](../vsto/deploying-an-office-solution.md).

### <a name="install-prerequisites"></a>Instalar pré-requisitos
 Antes que os usuários finais possam executar uma [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]solução que você cria usando as ferramentas de desenvolvimento do Office em , seus computadores devem ter certos pré-requisitos instalados. Se você implantar sua solução usando o ClickOnce ou criando um arquivo do Windows Installer, esses pré-requisitos podem ser instalados com a sua solução. Para obter mais informações, consulte [os pré-requisitos da solução do Office para implantação](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e) e [como: Instalar pré-requisitos em computadores do usuário final para executar soluções do Office.](https://msdn.microsoft.com/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)

### <a name="security"></a>Segurança
 A segurança para as soluções do VSTO [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office é aplicada por uma série de verificações que as marcas fazem quando instalam e carregam a solução. Essas verificações incluem verificar se a localização do manifesto de implantação é confiável ou se o certificado usado para assinar o manifesto de implantação é confiável. Para obter mais informações, consulte [soluções do Secure Office](../vsto/securing-office-solutions.md).

## <a name="see-also"></a>Confira também
- [Comece &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Comece a programar personalizações em nível de documento para excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md)
- [Comece a programar personalizações em nível de documento para o Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)
- [Comece a programar add-ins vsto](../vsto/getting-started-programming-vsto-add-ins.md)
