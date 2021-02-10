---
title: Arquitetura de personalizações em nível de documento
description: Saiba mais sobre os aspectos das personalizações em nível de documento, incluindo componentes de personalização e como as personalizações funcionam com Microsoft Office aplicativos.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VSTOLoader.dll
- formats [Office development in Visual Studio]
- file formats [Office development in Visual Studio]
- vstoee.dll
- managed code extensions [Office development in Visual Studio], definition
- document-level customizations [Office development in Visual Studio]
- AddInLoader.dll
- architecture [Office development in Visual Studio], document-level customizations
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a101fa597764538c0a1c09e7b4e5de2c81606346
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948720"
---
# <a name="architecture-of-document-level-customizations"></a>Arquitetura de personalizações em nível de documento
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] inclui projetos para a criação de personalizações em nível de documento para Microsoft Office Word e Microsoft Office Excel. Este tópico descreve os seguintes aspectos de personalizações em nível de documento:

- [Entender as personalizações](#UnderstandingCustomizations)

- [Componentes de personalizações](#Components)

- [Como as personalizações funcionam com Microsoft Office aplicativos](#HowCustomizationsWork)

  [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

  Para obter informações gerais sobre como criar personalizações em nível de documento, consulte [visão geral do desenvolvimento de soluções do Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md), introdução à [programação de personalizações em nível de documento para o Word](../vsto/getting-started-programming-document-level-customizations-for-word.md)e [introdução à programação de personalizações em nível de documento para o Excel](../vsto/getting-started-programming-document-level-customizations-for-excel.md).

## <a name="understand-customizations"></a><a name="UnderstandingCustomizations"></a> Entender as personalizações
 Quando você usa as ferramentas de desenvolvedor do Office no Visual Studio para criar uma personalização em nível de documento, você cria um assembly de código gerenciado que está associado a um documento específico. Um documento ou pasta de trabalho com um assembly vinculado é chamado de extensões de código gerenciado. Para obter mais informações, consulte [design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).

 Quando um usuário abre o documento, o assembly é carregado pelo aplicativo Microsoft Office. Depois que o assembly é carregado, a personalização pode responder a eventos enquanto o documento está aberto. A personalização também pode chamar o modelo de objeto para automatizar e estender o aplicativo enquanto o documento está aberto e pode usar qualquer uma das classes no [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] .

 O assembly se comunica com os componentes COM do aplicativo por meio do assembly de interoperabilidade primário do aplicativo. Para obter mais informações, consulte Visão geral de [assemblies de interoperabilidade principal do Office](../vsto/office-primary-interop-assemblies.md) e [desenvolvimento de soluções do Office &#40;&#41;do VSTO ](../vsto/office-solutions-development-overview-vsto.md).

 Se um usuário abrir várias personalizações em nível de documento ao mesmo tempo, cada assembly será carregado em um domínio de aplicativo diferente. Isso significa que uma solução que se comporta incorretamente não pode fazer com que outras soluções falhem. Personalizações em nível de documento são projetadas para funcionar com um único documento em um único domínio de aplicativo. Eles não são projetados para comunicação entre documentos. Para obter mais informações sobre domínios de aplicativo, consulte [domínios de aplicativo](/dotnet/framework/app-domains/application-domains).

> [!NOTE]
> As personalizações em nível de documento que você cria usando as ferramentas de desenvolvedor do Office no Visual Studio são projetadas para serem usadas somente quando o aplicativo é iniciado por um usuário final. Se o aplicativo for iniciado programaticamente, por exemplo, usando a automação, a personalização poderá não funcionar conforme o esperado.

### <a name="design-time-and-run-time-experiences"></a>Experiências de tempo de design e tempo de execução
 Para entender a arquitetura das personalizações em nível de documento, é útil entender as experiências de criar uma solução e executar uma solução.

#### <a name="design-time"></a>Tempo de design
 A experiência de tempo de design inclui as seguintes etapas:

1. O desenvolvedor cria um projeto de nível de documento no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . O projeto inclui o documento e o assembly que é executado atrás do documento. O documento pode já existir (criado por um designer) ou um novo documento pode ser criado junto com o projeto.

2. O designer — ou seja, o desenvolvedor que cria o projeto ou outra pessoa — cria a aparência final do documento para o usuário final.

#### <a name="runtime"></a>Runtime
 A experiência de tempo de execução inclui as seguintes etapas:

1. O usuário final abre um documento ou pasta de trabalho que tem extensões de código gerenciado.

2. O documento ou a pasta de trabalho carrega o assembly compilado.

3. O assembly responde a eventos enquanto o usuário trabalha no documento ou pasta de trabalho.

#### <a name="developer-and-end-user-perspective-compared"></a>Perspectiva do desenvolvedor e do usuário final comparada
 Como o desenvolvedor trabalha principalmente no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , e o usuário final trabalha no Word ou no Excel, há duas maneiras de entender as personalizações em nível de documento.

|Perspectiva do desenvolvedor|Perspectiva do usuário final|
|-----------------------------|----------------------------|
|Usando [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] o, o desenvolvedor grava o código que pode ser acessado no Word e no Excel.<br /><br /> Embora possa parecer que o desenvolvedor está criando um arquivo executável que executa o Word ou o Excel, o processo realmente funciona da mesma maneira. O documento está associado a um assembly e contém um ponteiro para esse assembly. Quando o documento é aberto, o Word ou Excel localiza o assembly e executa o código em resposta a todos os eventos manipulados.|Aqueles que usam a solução simplesmente abrem o documento ou a pasta de trabalho (ou criam um novo documento a partir de um modelo), assim como abriria qualquer outro arquivo de Microsoft Office.<br /><br /> O assembly fornece personalizações no documento ou pasta de trabalho, como preenchê-lo automaticamente com os dados atuais, ou mostrando uma caixa de diálogo para solicitar informações.|

### <a name="supported-document-formats-for-document-level-customizations"></a>Formatos de documento com suporte para personalizações em nível de documento
 Ao criar um projeto de personalização, você pode escolher o formato do documento que deseja usar no projeto. Para obter mais informações, consulte [como: criar projetos do Office no Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

 A tabela a seguir lista os formatos de documento que você pode usar em personalizações em nível de documento para Excel e Word.

|Excel|Word|
|-----------|----------|
|Pasta de trabalho do Excel (*. xlsx*)<br /><br /> Pasta de trabalho habilitada para macro do Excel (*. xlsm*)<br /><br /> Pasta de trabalho binária do Excel (*. xlsb*)<br /><br /> Pasta de trabalho do Excel 97-2003 (*. xls*)<br /><br /> Modelo do Excel (*. xltx*)<br /><br /> Modelo habilitado para macro do Excel (*. xltm*)<br /><br /> Modelo do Excel 97-2003 (*. xlt*)|Documento do Word (*. docx*)<br /><br /> Documento habilitado para macro do Word (*. docm*)<br /><br /> Documento do Word 97-2003 (*. doc*)<br /><br /> Modelo do Word (*. dotx*)<br /><br /> Modelo habilitado para macro do Word (*. dotm*)<br /><br /> Modelo do Word 97-2003 (*. dot*)|

 Você deve criar extensões de código gerenciado somente para documentos nos formatos com suporte. Caso contrário, determinados eventos podem não ser gerados quando o documento é aberto no aplicativo. Por exemplo, o <xref:Microsoft.Office.Tools.Excel.Workbook.Open> evento não é gerado quando você usa extensões de código gerenciado com pastas de trabalho salvas no formato de planilha XML do Excel ou na página da Web (*. htm*; *. html*) ao.

### <a name="support-for-word-documents-that-have-xml-file-name-extensions"></a>Suporte para documentos do Word que têm extensões de nome de arquivo. xml
 Os modelos de projeto de nível de documento não permitem que você crie projetos com base nos seguintes formatos de arquivo:

- Documento XML do Word (*\* XML*).

- Documento XML do Word 2003 (*\* XML*).

  Se você quiser que os usuários finais usem personalizações nesses formatos de arquivo, crie e implante uma personalização que usa um dos formatos de arquivo com suporte especificados na tabela acima. Depois de instalar a personalização, os usuários finais podem salvar o documento no formato de documento XML do Word (*\* XML*) ou no formato de documento XML (*\* XML*) do Word 2003 e a personalização continuará funcionando conforme o esperado.

## <a name="components-of-customizations"></a><a name="Components"></a> Componentes de personalizações
 Os principais componentes de uma personalização são o documento e o assembly. Além desses componentes, há várias outras partes que desempenham um papel importante em como Microsoft Office aplicativos descubram e carregam personalizações.

### <a name="deployment-manifest-and-application-manifest"></a>Manifesto de implantação e manifesto de aplicativo
 As personalizações usam manifestos de implantação e manifestos de aplicativo para identificar e carregar a versão mais atual do assembly de personalização. O manifesto de implantação aponta para o manifesto do aplicativo atual. O manifesto do aplicativo aponta para o assembly de personalização e especifica a classe de ponto de entrada (ou classes) a ser executada no assembly. Para obter mais informações, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

### <a name="visual-studio-tools-for-office-runtime"></a>Ferramentas do Visual Studio para o tempo de execução do Office
 Para executar personalizações em nível de documento que são criadas usando as ferramentas de desenvolvedor do Office no Visual Studio, os computadores do usuário final devem ter o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instalado. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] inclui componentes não gerenciados que carregam o assembly de personalização e também um conjunto de assemblies gerenciados. Esses assemblies gerenciados fornecem o modelo de objeto que seu código de personalização usa para automatizar e estender o aplicativo host.

 Para obter mais informações, consulte [visão geral do Visual Studio Tools for Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="how-customizations-work-with-microsoft-office-applications"></a><a name="HowCustomizationsWork"></a> Como as personalizações funcionam com Microsoft Office aplicativos
 Quando um usuário abre um documento que faz parte de uma Microsoft Office personalização, o aplicativo usa o manifesto de implantação que está vinculado ao documento para localizar e carregar a versão mais atual do assembly de personalização. O local do manifesto de implantação é armazenado em uma propriedade de documento personalizada chamada **AssemblyLocation**. A cadeia de caracteres que identifica esse local é inserida na propriedade quando você cria a solução.

 O manifesto de implantação aponta para o manifesto do aplicativo, que aponta para o assembly mais atual. Para obter mais informações, consulte [manifestos de aplicativo e implantação em soluções do Office](../vsto/application-and-deployment-manifests-in-office-solutions.md).

 A ilustração a seguir mostra a arquitetura básica de uma personalização em nível de documento.

 ![arquitetura de personalização do Office 2007](../vsto/media/office07-custom.png "arquitetura de personalização do Office 2007")

> [!NOTE]
> Nas soluções do Office direcionadas [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] para o, as soluções chamam o modelo de objeto do aplicativo host usando informações do tipo pia (assembly de interoperabilidade primária) inseridos no assembly da solução, em vez de chamar diretamente o pia. Para obter mais informações, consulte [design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="loading-process"></a>Processo de carregamento
 As etapas a seguir ocorrem quando um usuário abre um documento que faz parte de uma solução de Microsoft Office.

1. O aplicativo Microsoft Office verifica as propriedades do documento personalizado para ver se há extensões de código gerenciado associadas ao documento. Para obter mais informações, consulte [visão geral de propriedades de documento personalizadas](../vsto/custom-document-properties-overview.md).

2. Se houver extensões de código gerenciado, o aplicativo carregará *VSTOEE.dll*, que carrega *VSTOLoader.dll*. Essas são DLLs não gerenciadas que são os componentes do carregador para o tempo de execução das ferramentas do Visual Studio 2010 para Office. Para obter mais informações, consulte [visão geral do ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

3. *VSTOLoader.dll* carrega o [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)] e inicia a parte gerenciada do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

4. Se o documento for aberto de um local diferente do computador local, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] verificará se o local do documento está na lista **locais confiáveis** nas configurações da central de **confiabilidade** para esse aplicativo específico do Office. Se o local do documento não estiver em um local confiável, a personalização não será confiável e o processo de carregamento será interrompido aqui.

5. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] instalará a solução se ela ainda não tiver sido instalada, baixará os manifestos de aplicativo e implantação mais recentes e executará uma série de verificações de segurança. Para obter mais informações, consulte [proteger soluções do Office](../vsto/securing-office-solutions.md).

6. Se a personalização for confiável para ser executada, o [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] usará o manifesto de implantação e o manifesto do aplicativo para verificar se há atualizações de assembly. Se uma nova versão do assembly estiver disponível, o tempo de execução baixará a nova versão do assembly para o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] cache no computador cliente. Para obter mais informações, consulte [implantar uma solução do Office](../vsto/deploying-an-office-solution.md).

7. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] cria um novo domínio de aplicativo no qual carregar o assembly de personalização.

8. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] carrega o assembly de personalização no domínio do aplicativo.

9. O [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] chama o manipulador de eventos de **inicialização** em seu assembly de personalização. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).

## <a name="see-also"></a>Confira também
- [Arquitetura de soluções do Office no Visual Studio](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Arquitetura de suplementos do VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Visão geral do Ferramentas do Visual Studio para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md)
- [Proteger soluções do Office](../vsto/securing-office-solutions.md)
- [Projetar e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md)
- [Visão geral das propriedades do documento personalizado](../vsto/custom-document-properties-overview.md)
- [Dados armazenados em cache em personalizações em nível de documento](../vsto/cached-data-in-document-level-customizations.md)
