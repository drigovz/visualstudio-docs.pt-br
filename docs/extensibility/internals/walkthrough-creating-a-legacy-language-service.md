---
title: 'Passo a passo: Criando um serviço de linguagem legado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], creating
ms.assetid: 6a5dd2c2-261b-4efd-a3f4-8fb90b73dc82
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59ec18ab0c97ec89422e06f5b33804adcc750d5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703693"
---
# <a name="walkthrough-creating-a-legacy-language-service"></a>Passo a passo: criando um serviço de linguagem herdado
O uso das classes de idiomas managed package [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] framework (MPF) para implementar um serviço de idiomas é simples. Você precisa de um VSPackage para hospedar o serviço de idiomas, o serviço de idioma em si e um analisador para o seu idioma.

## <a name="prerequisites"></a>Pré-requisitos
 Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Visual Studio SDK](../../extensibility/visual-studio-sdk.md).

## <a name="locations-for-the-visual-studio-package-project-template"></a>Locais para o modelo de projeto do pacote visual studio
 O Modelo de Projeto de Pacote do Visual Studio pode ser encontrado em três locais de modelo diferentes na caixa de diálogo **Novo Projeto:**

1. Em Extensibilidade Básica Visual. A linguagem padrão do projeto é Visual Basic.

2. Sob C# Extensibilidade. A linguagem padrão do projeto é C#.

3. Em Outros Tipos de Projeto Extensibilidade. A linguagem padrão do projeto é C++.

### <a name="create-a-vspackage"></a>Criar um VSPackage

1. Crie um novo VSPackage com o modelo de projeto Visual Studio Package.

    Se você estiver adicionando um serviço de idioma a um VSPackage existente, pule as etapas a seguir e vá diretamente para o procedimento "Criar a classe de serviço de idioma".

2. Digite MyLanguagePackage para o nome do projeto e clique em **OK**.

    Você pode usar o nome que quiser. Esses procedimentos detalhados aqui assumem myLanguagePackage como o nome.

3. Selecione [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] como o idioma e a opção de gerar um novo arquivo-chave. Clique em **Próximo**.

4. Digite as informações apropriadas da empresa e do pacote. Clique em **Próximo**.

5. Selecione **Menu 'Menu'.** Clique em **Próximo**.

    Se você não pretende suportar trechos de código, basta clicar em Concluir e ignorar o próximo passo.

6. Digite **'Inserir snippet'** como nome **de comando** e `cmdidInsertSnippet` para o **ID de comando**. Clique em **Concluir**.

    O **Nome de Comando** e o **ID de Comando** podem ser o que você quiser, estes são apenas exemplos.

### <a name="create-the-language-service-class"></a>Crie a classe de serviço de idiomas

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto MyLanguagePackage, escolha **Adicionar**, **Referência**e, em seguida, escolha o botão Adicionar **nova referência.**

2. Na caixa de diálogo **Adicionar referência,** selecione **Microsoft.VisualStudio.Package.LanguageService** na guia **.NET** e clique em **OK**.

     Isso precisa ser feito apenas uma vez para o projeto do pacote de idiomas.

3. No **Solution Explorer,** clique com o botão direito do mouse no projeto VSPackage e selecione **Adicionar,** **Classe**.

4. Certifique-se de que **a classe** está selecionada na lista de modelos.

5. Digite **MyLanguageService.cs** para o nome do arquivo de classe e clique **em Adicionar**.

     Você pode usar o nome que quiser. Estes procedimentos `MyLanguageService` detalhados aqui assumem como o nome.

6. No arquivo MyLanguageService.cs, adicione `using` as seguintes diretivas.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_1.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#1](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_1.vb)]

7. Modificar `MyLanguageService` a classe para <xref:Microsoft.VisualStudio.Package.LanguageService> derivar da classe:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_2.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#2](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_2.vb)]

8. Posicione o cursor em "LanguageService" e no menu **Editar**, **IntelliSense,** selecione **Implementar classe abstrata**. Isso adiciona os métodos mínimos necessários para implementar uma classe de serviço de idiomas.

9. Implemente os métodos abstratos descritos na [implementação de um serviço de linguagem legado](../../extensibility/internals/implementing-a-legacy-language-service2.md).

### <a name="register-the-language-service"></a>Registre o Serviço de Idiomas

1. Abra o arquivo MyLanguagePackagePackage.cs `using` e adicione as seguintes diretivas:

     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_3.vb)]
     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#3](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_3.cs)]

2. Registre sua classe de serviço de idioma conforme descrito no [registro de um serviço de idioma legado](../../extensibility/internals/registering-a-legacy-language-service1.md). Isso inclui os atributos ProvideXX e as seções "Proffering the Language Service". Use myLanguageService onde este tópico usa TestLanguageService.

### <a name="the-parser-and-scanner"></a>O Analisador e o Scanner

1. Implemente um analisador e um scanner para o seu idioma, conforme descrito no [Analisador de Serviços de Linguagem Legado e scanner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

     Como você implementa seu analisador e scanner depende inteiramente de você e está além do escopo deste tópico.

## <a name="language-service-features"></a>Recursos de serviço de idioma
 Para implementar cada recurso no serviço de idiomas, você normalmente obtém uma classe da classe de serviço de idioma súti-lana, implementa quaisquer métodos abstratos conforme necessário e anula os métodos apropriados. Quais classes você cria e/ou deriva depende dos recursos que você pretende suportar. Esses recursos são discutidos detalhadamente nos [Recursos de Serviço de Linguagem Legado .](../../extensibility/internals/legacy-language-service-features1.md) O procedimento a seguir é a abordagem geral para a obtenção de uma classe das classes do MPF.

#### <a name="deriving-from-an-mpf-class"></a>Oriundos de uma classe do MPF

1. No **Solution Explorer,** clique com o botão direito do mouse no projeto VSPackage e selecione **Adicionar,** **Classe**.

2. Certifique-se de que **a classe** está selecionada na lista de modelos.

     Digite um nome adequado para o arquivo de classe e clique **em Adicionar**.

3. No novo arquivo de classe, adicione as seguintes `using` diretivas.

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_4.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#4](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_4.vb)]

4. Modifique a classe para derivar da classe mpf desejada.

5. Adicione um construtor de classe que pegue pelo menos os mesmos parâmetros do construtor da classe base e passe os parâmetros do construtor para o construtor da classe base.

     Por exemplo, o construtor de uma <xref:Microsoft.VisualStudio.Package.Source> classe derivada da classe pode parecer o seguinte:

     [!code-csharp[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/CSharp/walkthrough-creating-a-legacy-language-service_5.cs)]
     [!code-vb[CreatingALanguageService(ManagedPackageFramework)#5](../../extensibility/internals/codesnippet/VisualBasic/walkthrough-creating-a-legacy-language-service_5.vb)]

6. No menu **Editar**, **IntelliSense,** **selecione Implementar classe abstrata** se a classe base tiver algum método abstrato que deve ser implementado.

7. Caso contrário, posicione o cuidador dentro da classe e digite o método a ser substituído.

     Por exemplo, `public override` digite para ver uma lista de todos os métodos que podem ser substituídos nessa classe.

## <a name="see-also"></a>Confira também
- [Implementando um serviço de linguagem herdado](../../extensibility/internals/implementing-a-legacy-language-service1.md)
