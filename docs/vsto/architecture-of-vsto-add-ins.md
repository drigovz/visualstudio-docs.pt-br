---
title: Arquitetura de suplementos do VSTO
description: Os suplementos do VSTO criados no Visual Studio têm recursos arquitetônicos que enfatizam a estabilidade e a segurança e permitem que eles trabalhem junto com Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- architecture [Office development in Visual Studio], application-level add-ins
- vstoee.dll
- application-level add-ins [Office development in Visual Studio], architecture
- add-ins [Office development in Visual Studio], architecture
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 136903bd6d844d57ef06fce5a62506e026355509
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882603"
---
# <a name="architecture-of-vsto-add-ins"></a>Arquitetura de suplementos do VSTO
  Os suplementos do VSTO criados usando as ferramentas de desenvolvedor do Office no Visual Studio têm recursos arquitetônicos que enfatizam a estabilidade e a segurança e permitem que eles trabalhem junto com Microsoft Office. Este tópico descreve os seguintes aspectos dos suplementos do VSTO:

- [Entender os suplementos do VSTO](#UnderstandingAddIns)

- [Componentes de suplementos do VSTO](#AddinComponents)

- [Como os suplementos do VSTO funcionam com Microsoft Office aplicativos](#HowAddinsWork)

  [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

  Para obter informações gerais sobre como criar suplementos do VSTO, consulte [visão geral do desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) e comece [a programar suplementos do VSTO](../vsto/getting-started-programming-vsto-add-ins.md).

## <a name="understand-vsto-add-ins"></a><a name="UnderstandingAddIns"></a> Entender os suplementos do VSTO
 Quando você usa as ferramentas de desenvolvedor do Office no Visual Studio para criar um suplemento do VSTO, você cria um assembly de código gerenciado que é carregado por um aplicativo Microsoft Office. Depois que o assembly é carregado, o suplemento do VSTO pode responder a eventos que são gerados no aplicativo (por exemplo, quando um usuário clica em um item de menu). O suplemento do VSTO também pode chamar o modelo de objeto para automatizar e estender o aplicativo e pode usar qualquer uma das classes no [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

 O assembly se comunica com os componentes COM do aplicativo por meio do assembly de interoperabilidade primário do aplicativo. Para obter mais informações, consulte Visão geral de [assemblies de interoperabilidade principal do Office](../vsto/office-primary-interop-assemblies.md) e [desenvolvimento de soluções do Office &#40;&#41;do VSTO ](../vsto/office-solutions-development-overview-vsto.md).

 Se vários suplementos do VSTO forem instalados para um aplicativo, cada suplemento do VSTO será carregado em um domínio de aplicativo diferente. Isso significa que um suplemento do VSTO que se comporta incorretamente não pode fazer com que outros suplementos do VSTO falhem. Também ajuda a garantir que, quando o aplicativo for fechado, todos os assemblies do suplemento do VSTO sejam descarregados da memória. Para obter mais informações sobre domínios de aplicativo, consulte [domínios de aplicativo](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> Os suplementos do VSTO que você cria usando as ferramentas de desenvolvedor do Office no Visual Studio são projetados para serem usados somente quando o host Microsoft Office aplicativo é iniciado por um usuário final. Se o aplicativo for iniciado programaticamente (por exemplo, usando automação), o suplemento do VSTO poderá não funcionar conforme o esperado.

## <a name="components-of-vsto-add-ins"></a><a name="AddinComponents"></a> Componentes de suplementos do VSTO
 Embora o assembly do suplemento do VSTO seja o principal componente, há vários outros componentes que desempenham um papel importante em como Microsoft Office aplicativos detectam e carregam suplementos do VSTO.

### <a name="registry-entries"></a>Entradas do Registro
 Microsoft Office aplicativos detectam suplementos do VSTO procurando um conjunto de entradas do registro. Para obter uma lista completa das entradas do registro usadas pelos suplementos do VSTO, consulte [entradas do registro para suplementos do VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

 Quando você cria sua solução, o Visual Studio cria todas as entradas de Registro necessárias no computador de desenvolvimento para que você possa depurar e executar o suplemento do VSTO. Para obter mais informações, consulte [criar soluções do Office](../vsto/building-office-solutions.md).

 Se você usar o ClickOnce para implantar sua solução, o programa de instalação gerado pelo processo de publicação criará automaticamente as chaves do registro no computador do usuário final. Para obter mais informações, consulte [implantar uma solução do Office usando o ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).

### <a name="deployment-manifest-and-application-manifest"></a>Manifesto de implantação e manifesto de aplicativo
 Os suplementos do VSTO usam manifestos de implantação e manifestos de aplicativo para identificar e carregar a versão mais atual do assembly de suplemento do VSTO. O manifesto de implantação aponta para o manifesto do aplicativo atual. O manifesto do aplicativo aponta para o assembly do suplemento do VSTO e especifica a classe de ponto de entrada a ser executada no assembly. Para obter mais informações, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

### <a name="visual-studio-tools-for-office-runtime"></a>Ferramentas do Visual Studio para o tempo de execução do Office
 Para executar os suplementos do VSTO que são criados usando as ferramentas de desenvolvedor do Office no Visual Studio, os computadores do usuário final devem ter o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instalado. O tempo de execução inclui componentes não gerenciados e um conjunto de assemblies gerenciados. Os componentes não gerenciados carregam o assembly do suplemento do VSTO. Os assemblies gerenciados fornecem o modelo de objeto que seu código de suplemento do VSTO usa para automatizar e estender o aplicativo host.

 Para obter mais informações, consulte [visão geral do ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-vsto-add-ins-work-with-microsoft-office-applications"></a><a name="HowAddinsWork"></a> Como os suplementos do VSTO funcionam com Microsoft Office aplicativos
 Quando um usuário inicia um aplicativo Microsoft Office, o aplicativo usa o manifesto de implantação e o manifesto do aplicativo para localizar e carregar a versão mais atual do assembly do suplemento do VSTO. A ilustração a seguir mostra a arquitetura básica desses suplementos do VSTO.

 ![arquitetura de suplemento do Office 2007](../vsto/media/office07addin.png "arquitetura de suplemento do Office 2007")

> [!NOTE]
> Em soluções do Office direcionadas ao [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou ao [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , as soluções chamam o modelo de objeto do aplicativo host usando informações de tipo de pia inseridas no assembly da solução, em vez de chamar diretamente o pia. Para obter mais informações, consulte [design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Processo de carregamento
 As etapas a seguir ocorrem quando um usuário inicia um aplicativo:

1. O aplicativo verifica o registro em busca de entradas que identificam os suplementos do VSTO que foram criados usando as ferramentas de desenvolvedor do Office no Visual Studio.

2. Se o aplicativo encontrar essas entradas de registro, o aplicativo carregará VSTOEE.dll, que carrega VSTOLoader.dll. Essas são DLLs não gerenciadas que são os componentes do carregador para o tempo de execução das ferramentas do Visual Studio 2010 para Office. Para obter mais informações, consulte [visão geral do ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* carrega o [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] e inicia a parte gerenciada do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verifica se há atualizações de manifesto e baixa os manifestos de aplicativo e implantação mais recentes.

5. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] executa uma série de verificações de segurança. Para obter mais informações, consulte [proteger soluções do Office](../vsto/securing-office-solutions.md).

6. Se o suplemento do VSTO for confiável para ser executado, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usará o manifesto de implantação e o manifesto do aplicativo para verificar se há atualizações de assembly. Se uma nova versão do assembly estiver disponível, o tempo de execução baixará a nova versão do assembly para o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] cache no computador cliente. Para obter mais informações, consulte [implantar uma solução do Office](../vsto/deploying-an-office-solution.md).

7. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cria um novo domínio de aplicativo no qual carregar o assembly de suplemento do VSTO.

8. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] carrega o assembly do suplemento do VSTO no domínio do aplicativo.

9. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> método em seu suplemento do VSTO, se você o tiver substituído.

     Opcionalmente, você pode substituir esse método para expor um objeto em seu suplemento do VSTO para outras soluções de Microsoft Office. Para obter mais informações, consulte [chamar código em suplementos do VSTO de outras soluções do Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

10. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método em seu suplemento do VSTO, se você o tiver substituído.

     Opcionalmente, você pode substituir esse método para estender um recurso de Microsoft Office retornando um objeto que implementa uma interface de extensibilidade. Para obter mais informações, consulte [personalizar recursos da interface do usuário usando interfaces de extensibilidade](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

    > [!NOTE]
    > O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] faz chamadas separadas para o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método para cada interface de extensibilidade que é suportada pelo aplicativo host. Embora a primeira chamada para o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método geralmente ocorra antes da chamada para o `ThisAddIn_Startup` método, o suplemento do VSTO não deve fazer suposições sobre quando o <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> método será chamado ou quantas vezes ele será chamado.

11. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o `ThisAddIn_Startup` método em seu suplemento do VSTO. Esse método é o manipulador de eventos padrão para o <xref:Microsoft.Office.Tools.AddInBase.Startup> evento. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Confira também
- [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Arquitetura de personalizações em nível de documento](../vsto/architecture-of-document-level-customizations.md)
- [Visão geral do Ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md)
- [Desenvolver soluções do Office](../vsto/developing-office-solutions.md)
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
- [Implantar uma solução do Office](../vsto/deploying-an-office-solution.md)
