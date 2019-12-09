---
title: Escrever código em soluções do Office
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cead0569ae067fcc503f7f2074807c609e6eed75
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255041"
---
# <a name="write-code-in-office-solutions"></a>Escrever código em soluções do Office
  Há alguns aspectos de escrever código em projetos do Office que são diferentes de outros tipos de projetos no Visual Studio. Muitas dessas diferenças estão relacionadas à maneira como os modelos de objeto do Office são expostos ao código gerenciado. Outras diferenças estão relacionadas ao design de projetos do Office.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>Código gerenciado e programação do Office
 A principal tecnologia que torna a criação de uma solução de Microsoft Office integrada possível é a automação, que faz parte da tecnologia de Component Object Model (COM). A automação permite que você use código para criar e controlar objetos de software expostos por qualquer aplicativo, DLL ou controle ActiveX que dê suporte às interfaces programáticas apropriadas.

### <a name="understand-primary-interop-assemblies"></a>Entender os assemblies de interoperabilidade primária
 Microsoft Office aplicativos expõem grande parte de sua funcionalidade à automação. No entanto, você não pode usar código gerenciado (como C#Visual Basic ou) diretamente para automatizar aplicativos do Office. Para automatizar aplicativos do Office usando código gerenciado, você deve usar os PIAs (assemblies de interoperabilidade primária do Office). Os assemblies de interoperabilidade primários permitem que o código gerenciado interaja com o modelo de objeto baseado em COM dos aplicativos do Office.

 Cada aplicativo de Microsoft Office tem um PIA. Quando você cria um projeto do Office no Visual Studio, uma referência ao PIA apropriado é adicionada automaticamente ao projeto. Para automatizar os recursos de outros aplicativos do Office a partir do projeto, você deve adicionar manualmente uma referência ao PIA apropriado. Para obter mais informações, confira [Como: Direcione aplicativos do Office por meio de](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)assemblies de interoperabilidade primária.

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>Usar assemblies de interoperabilidade primários em tempo de design e Runtime
 Você deve ter os PIAs do Office instalados e registrados no cache de assembly global em seu computador de desenvolvimento para executar a maioria das tarefas de desenvolvimento. Para obter mais informações, consulte [configurar um computador para desenvolver soluções do Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).

 Os pias do Office não são necessários nos computadores dos usuários finais para executar as soluções do Office [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] direcionadas para o ou posterior. Para obter mais informações, consulte [design e criar soluções do Office](../vsto/designing-and-creating-office-solutions.md).

### <a name="use-types-in-primary-interop-assemblies"></a>Usar tipos em assemblies de interoperabilidade primários
 Os PIAs do Office contêm uma combinação de tipos que expõem o modelo de objeto dos aplicativos do Office e tipos de infraestrutura adicionais que não se destinam a serem usados diretamente no seu código. Para obter uma visão geral dos tipos nos PIAs do Office, consulte [visão geral de classes e interfaces nos assemblies de interoperabilidade primária do Office](/previous-versions/office/office-12/ms247299\(v\=office.12\)).

 Como os tipos nos PIAs do Office correspondem aos tipos nos modelos de objeto baseados em COM, a maneira como você usa esses tipos é geralmente diferente de outros tipos gerenciados. Por exemplo, a maneira como você chama métodos que têm parâmetros opcionais em um assembly de interoperabilidade primário do Office depende da linguagem de programação que você está usando em seu projeto. Para mais informações, consulte os seguintes tópicos:

- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md).

- [Associação tardia nas soluções do Office](../vsto/late-binding-in-office-solutions.md).

## <a name="program-model-of-office-projects"></a>Modelo de programa de projetos do Office
 Todos os projetos do Office incluem uma ou mais classes geradas que fornecem o ponto de entrada para seu código. Essas classes também fornecem acesso ao modelo de objeto do aplicativo host e acesso a recursos como painéis de ações e painéis de tarefas personalizados.

### <a name="understand-the-generated-classes"></a>Entender as classes geradas
 Em projetos de nível de documento para Excel e Word, a classe gerada é semelhante a um objeto de nível superior no modelo de objeto do aplicativo. Por exemplo, a classe `ThisDocument` gerada em um projeto de documento do Word fornece os mesmos membros <xref:Microsoft.Office.Interop.Word.Document> que a classe no modelo de objeto do Word. Para obter mais informações sobre as classes geradas em projetos de nível de documento, consulte [programar personalizações em nível de documento](../vsto/programming-document-level-customizations.md).

 Os projetos de suplemento do VSTO fornecem uma classe gerada `ThisAddIn`chamada. Essa classe não se assemelha a uma classe no modelo de objeto do aplicativo host. Em vez disso, essa classe representa o suplemento do VSTO e fornece membros que você pode usar para acessar o modelo de objeto do aplicativo host e acessar outros recursos disponíveis para os suplementos do VSTO. Para obter mais informações, consulte [programar suplementos do VSTO](../vsto/programming-vsto-add-ins.md).

 Todas as classes geradas em projetos `Startup` do `Shutdown` Office incluem manipuladores de eventos e. Para começar a escrever o código, você normalmente adiciona código a esses manipuladores de eventos. Para inicializar o suplemento do VSTO, você pode adicionar código ao manipulador de `Startup` eventos. Para limpar os recursos usados pelo suplemento do VSTO, você pode adicionar código ao manipulador de `Shutdown` eventos. Para obter mais informações, consulte [eventos em projetos do Office](../vsto/events-in-office-projects.md).

### <a name="access-the-generated-classes-at-run-time"></a>Acessar as classes geradas em tempo de execução
 Quando uma solução do Office é carregada, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] o cria uma instância de cada uma das classes geradas em seu projeto. Você pode acessar esses objetos de qualquer código em seu projeto usando a `Globals` classe. Por exemplo, você pode usar a `Globals` classe para chamar o código na `ThisAddIn` classe a partir de um manipulador de eventos de um botão da faixa de das de um suplemento do VSTO.

 Para obter mais informações, consulte [acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md).

### <a name="namespace-considerations-in-office-solutions"></a>Considerações de namespace em soluções do Office
 Você não pode alterar o *namespace padrão* (ou o *namespace raiz* em Visual Basic) de um projeto do Office depois de criar o projeto. O namespace padrão sempre corresponderá ao nome do projeto especificado quando você criou o projeto. Se você renomear o projeto, o namespace padrão não será alterado. Para obter mais informações sobre o namespace padrão em projetos, consulte [página do aplicativo, &#40;designer&#35; do projeto C](../ide/reference/application-page-project-designer-csharp.md) e [página do &#40;aplicativo&#41;, designer de projeto Visual Basic](../ide/reference/application-page-project-designer-visual-basic.md).

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>Alterar o namespace das classes de item de C# host em projetos
 As classes de item de host (por `ThisAddIn`exemplo `ThisWorkbook`, as `ThisDocument` classes, ou) têm seus próprios namespaces C# em projetos do Visual Office. Por padrão, o namespace para itens de host em seu projeto corresponde ao nome do projeto que você especificou quando criou o projeto.

 Para alterar o namespace dos itens do host em um projeto C# do Visual Office, use o namespace para a propriedade do **item de host** . Para obter mais informações, consulte [Propriedades em projetos do Office](../vsto/properties-in-office-projects.md).

## <a name="supported-programming-languages-in-office-projects"></a>Linguagens de programação com suporte em projetos do Office
 Os modelos de projeto do Office no Visual Studio dão suporte apenas às C# linguagens de programação Visual Basic e Visual. Portanto, esses modelos de projeto estão disponíveis somente sob os nós **Visual Basic** e  **C# Visual** da caixa de diálogo **novo projeto** no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Para obter mais informações, confira [Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

## <a name="language-choice-and-office-programming"></a>Escolha de idioma e programação do Office
 Microsoft Office e Visual Basic for Applications (VBA) foram desenvolvidos para trabalhar em conjunto para otimizar o fluxo de trabalho de personalização do aplicativo. Visual Basic herdou alguns desses desenvolvimentos. Por exemplo, Visual Basic dá suporte a parâmetros opcionais, o que significa que você pode escrever menos código ao chamar alguns métodos na Microsoft Office assemblies de interoperabilidade C#primária do que ao usar o Visual.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Programa com Visual Basic vs. Visual C# nas soluções do Office
 Você pode criar soluções do Office usando o Visual Basic ou o C#Visual. Como os modelos de objeto Microsoft Office foram projetados para serem usados com o Microsoft Visual Basic for Applications (VBA), Visual Basic desenvolvedores podem trabalhar confortavelmente com os objetos expostos pelos aplicativos Microsoft Office. Os C# desenvolvedores visuais podem usar a maioria dos mesmos recursos que Visual Basic desenvolvedores, mas há alguns casos em que eles devem escrever código adicional para usar os modelos de objeto do Office. Há também algumas diferenças entre os recursos de programação básica no desenvolvimento do Office e o código gerenciado escrito C#em Visual Basic e.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Principais diferenças entre Visual Basic e VisualC#
<!-- markdownlint-enable MD003 MD020 -->

A tabela a seguir mostra as principais diferenças entre Visual Basic C# e o Visual no desenvolvimento do Office.

|Recurso|Descrição|Suporte a Visual Basic|Suporte C# Visual|
|-------------|-----------------|--------------------------|------------------------|
|Parâmetros opcionais|Muitos métodos de Microsoft Office têm parâmetros que não são necessários quando você chama o método. Se nenhum valor for passado para o parâmetro, será usado um valor padrão.|Visual Basic dá suporte a parâmetros opcionais.|O C# Visual dá suporte a parâmetros opcionais na maioria dos casos. Para obter mais informações, consulte [parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md).|
|Passando parâmetros por referência|Parâmetros opcionais na maioria dos Microsoft Office assemblies de interoperabilidade primária podem ser passados por valor. No entanto, em alguns assemblies de interoperabilidade primários, os parâmetros opcionais que aceitam tipos de referência devem ser passados por referência.<br /><br /> Para obter mais informações sobre parâmetros de tipo de referência e valor, consulte [passar argumentos por valor &#40;e&#41; por referência Visual Basic](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (para Visual Basic) e [passar parâmetros &#40;C&#35; guia&#41;de programação](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).|Nenhum trabalho adicional é necessário para passar parâmetros por referência. O compilador Visual Basic passa automaticamente os parâmetros por referência, quando necessário.|Na maioria dos casos, o C# compilador Visual passa automaticamente os parâmetros por referência quando necessário. Para obter mais informações, consulte [parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md).|
|Propriedades parametrizadas|Algumas propriedades aceitam parâmetros e agem como funções somente leitura.|Visual Basic dá suporte a propriedades que aceitam parâmetros.|O C# Visual oferece suporte a propriedades que aceitam parâmetros.|
|Associação tardia|A associação tardia envolve determinar as propriedades de objetos em tempo de execução, em vez de converter variáveis para o tipo de objeto no tempo de design.|Visual Basic executa a associação tardia quando **Option Strict** é off. Quando **Option Strict** está on, você deve converter explicitamente objetos e usar tipos no <xref:System.Reflection> namespace para acessar membros de associação tardia. Para obter mais informações, consulte [associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md).|O C# Visual executa associação tardia em projetos direcionados [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]para o. Para obter mais informações, consulte [associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md).|

## <a name="key-differences-between-office-development-and-managed-code"></a>Principais diferenças entre o desenvolvimento do Office e o código gerenciado
 A tabela a seguir mostra as principais diferenças entre o desenvolvimento do Office e o código gerenciado C#escrito em Visual Basic ou Visual.

|Recurso|Descrição|Suporte ao Visual Basic C# e ao Visual|
|-------------|-----------------|-----------------------------------------|
|Índices de matriz|O limite de matriz inferior de coleções em aplicativos Microsoft Office começa com 1. Visual Basic e Visual C# usam matrizes baseadas em 0. Para obter mais informações, [consulte &#40;guia&#35; &#41; de programação C de matrizes](/dotnet/csharp/programming-guide/arrays/index) e [matrizes em Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/index).|Para acessar o primeiro item de uma coleção no modelo de objeto de um aplicativo Microsoft Office, use o índice 1 em vez de 0.|

## <a name="see-also"></a>Consulte também

- [Parâmetros opcionais em soluções do Office](../vsto/optional-parameters-in-office-solutions.md)
- [Acesso global a objetos em projetos do Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Eventos em projetos do Office](../vsto/events-in-office-projects.md)
- [Como: Direcionar aplicativos do Office por meio de assemblies de interoperabilidade primária](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [Como: Criar manipuladores de eventos em projetos do Office](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Associação tardia em soluções do Office](../vsto/late-binding-in-office-solutions.md)
- [Desenvolvimento colaborativo de soluções do Office](../vsto/collaborative-development-of-office-solutions.md)
