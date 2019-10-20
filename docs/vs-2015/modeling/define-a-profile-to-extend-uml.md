---
title: Definir um perfil para estender o UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- profiles, UML
- stereotypes, UML
- UML, profiles and stereotypes
- UML - extending, defining profiles
- UML, customizing
- UML, profiles
ms.assetid: 776589cb-f89d-48d5-aafa-04a4c074b0d6
caps.latest.revision: 44
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e621297b36d75a0e48baed4ab24d50abd5e61663
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668684"
---
# <a name="define-a-profile-to-extend-uml"></a>Definir um perfil para estender UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode definir um *perfil UML* para personalizar os elementos do modelo padrão para fins específicos. Um perfil define um ou mais *estereótipos UML*. Um estereótipo pode ser usado para marcar um tipo como representando um determinado tipo de objeto. Um estereótipo também pode estender a lista de propriedades de um elemento.

 Vários perfis são instalados com as edições com suporte do Visual Studio. Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport). Para obter mais informações sobre esses perfis e sobre como aplicar estereótipos, consulte [personalizar seu modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

 Você pode definir seus próprios perfis para adaptar e estender o UML para sua própria área de negócios ou arquitetura. Por exemplo:

- Se você definir com frequência sites da Web, poderá definir seu próprio perfil que fornece um estereótipo «webpage» que pode ser aplicado a classes em diagramas de classe. Em seguida, você pode usar diagramas de classe para planejar um site da Web. Toda classe «webpage» teria Propriedades extras para o conteúdo da página, o estilo e assim por diante.

- Se você desenvolver um software de banco, poderá definir um perfil que forneça um estereótipo «Account». Em seguida, você pode usar diagramas de classe para definir diferentes tipos de conta e mostrar as relações entre eles.

  Você pode distribuir seus próprios perfis para sua equipe. Cada membro da equipe pode instalar seu perfil. Isso permite que eles editem e criem modelos que usam seus estereótipos.

> [!NOTE]
> Se você aplicar os estereótipos de um perfil em um modelo que você está editando e, em seguida, compartilhar o modelo com outras pessoas, eles deverão instalar o mesmo perfil em seus próprios computadores. Caso contrário, eles não poderão ver os estereótipos que você usou.

 Um perfil geralmente faz parte de uma extensão maior de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Por exemplo, você pode definir um comando que traduz algumas partes de um modelo para codificar. Você pode definir um perfil que os usuários devem aplicar aos pacotes que desejam converter. Você distribuiria o novo comando junto com o perfil em uma única extensão de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

 Você também pode definir variantes localizadas de um perfil. Os usuários que carregam sua extensão veem a variante apropriada para sua própria cultura.

## <a name="DefineProfile"></a>Como definir um perfil

#### <a name="to-define-a-uml-profile"></a>Para definir um perfil UML

1. Crie um novo arquivo XML com a extensão de nome de arquivo `.profile`.

2. Adicione definições de estereótipo de acordo com as diretrizes descritas na [estrutura de um perfil](#Schema).

3. Adicione o perfil a uma extensão do Visual Studio (arquivo de `.vsix`). Você pode criar uma nova extensão para seu perfil ou adicionar o perfil a uma extensão existente.

     Consulte a próxima seção, [como adicionar um perfil a uma extensão do Visual Studio](#AddProfile).

4. Instale a extensão no seu computador.

    1. Clique duas vezes no arquivo de extensão, que tem uma extensão de nome de arquivo `.vsix`.

    2. Reinicie o Visual Studio.

5. Verifique se o perfil foi instalado.

    1. Selecione o modelo no Gerenciador UML.

    2. Na janela Propriedades, clique na propriedade **perfis** . Seu perfil será exibido no menu. Defina a marca de seleção ao lado do perfil.

    3. Selecione um elemento para o qual seu perfil define estereótipos. Na janela Propriedades, clique na propriedade **estereótipos** . Seus estereótipos aparecerão na lista. Defina a marca de seleção em um dos estereótipos.

    4. Se o seu perfil definir propriedades adicionais para esse estereótipo, expanda a propriedade estereótipo para vê-las.

6. Envie o arquivo de extensão para outros usuários do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para instalar em seus computadores.

## <a name="AddProfile"></a>Como adicionar um perfil a uma extensão do Visual Studio
 Para instalar um perfil e permitir que você o envie a outros usuários, você deve adicionar o perfil a uma extensão do Visual Studio. Para obter mais informações, consulte [implantando extensões do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=160780).

#### <a name="to-define-a-profile-in-a-new-visual-studio-extension"></a>Para definir um perfil em uma nova extensão do Visual Studio

1. Crie um projeto de extensão do Visual Studio.

   > [!NOTE]
   > Você deve ter instalado [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] para usar este procedimento.

   1. No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.

   2. Na caixa de diálogo **novo projeto** , em **modelos instalados**, expanda **Visual C#** , clique em **extensibilidade**e clique em **projeto VSIX**. Defina o nome do projeto e clique em **OK**.

2. Adicione seu perfil ao projeto.

   - Em Gerenciador de Soluções, clique com o botão direito do mouse no projeto, aponte para **Adicionar**e clique em **Item existente**. Na caixa de diálogo, localize o arquivo de perfil.

3. Defina a propriedade **copiar para saída** do arquivo de perfil.

   1. Em Gerenciador de Soluções, clique com o botão direito do mouse no arquivo de perfil e clique em **Propriedades**.

   2. Na janela Propriedades, defina a propriedade **copiar para diretório de saída** como **copiar sempre**.

4. Em Gerenciador de Soluções, abra `source.extension.vsixmanifest`.

    O arquivo é aberto no editor de manifesto de extensão.

5. Na página **ativos** , adicione uma linha que descreve o perfil:

   - Clique em **Novo**. Defina os campos na caixa de diálogo **Adicionar novo ativo** da seguinte maneira.

   - Defina o **tipo** como `Microsoft.VisualStudio.UmlProfile`

        Essa não é uma das opções suspensas. Insira esse nome no teclado.

   - Clique em **arquivo no sistema de arquivos** e selecione o nome do seu arquivo de perfil, por exemplo `MyProfile.profile`

6. Compile o projeto.

7. **Para depurar o perfil**, pressione F5.

    Uma instância experimental do Visual Studio é aberta. Nessa instância, abra um projeto de modelagem. No Gerenciador UML, selecione o elemento raiz do modelo e, na janela Propriedades, selecione seu perfil. Em seguida, selecione elementos dentro do modelo e defina estereótipos que você definiu para eles.

8. **Para extrair o VSIX para implantação**

   1. No Windows Explorer, abra a pasta **.\bin\Debug** ou **.\bin\Release** para localizar o arquivo **. vsix** . Este é um arquivo de extensão [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Ele pode ser instalado em seu computador e enviado a outros usuários do Visual Studio.

   2. Para instalar a extensão:

       1. Clique duas vezes no arquivo `.vsix`. O instalador de extensão do Visual Studio será iniciado.

       2. Reinicie todas as instâncias do Visual Studio em execução.

   O procedimento alternativo a seguir pode ser usado para extensões pequenas se você não tiver instalado [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].

#### <a name="to-define-a-profile-extension-without-using-visual-studio-sdk"></a>Para definir uma extensão de perfil sem usar o SDK do Visual Studio

1. Crie um diretório do Windows que contenha os três seguintes arquivos:

    - @No__t_1 *YourProfile*

    - `extension.vsixmanifest`

    - `[Content_Types].xml`-digite esse nome como mostrado aqui, com os colchetes

2. Edite `[Content_Types].xml` para conter o texto a seguir. Observe que ele contém uma entrada para cada extensão de nome de arquivo.

    ```
    <?xml version="1.0" encoding="utf-8"?>
    <Types xmlns="http://schemas.openxmlformats.org/package/2006/content-types">
      <Default Extension="profile" ContentType="application/octet-stream" />
      <Default Extension="vsixmanifest" ContentType="text/xml" />
    </Types>
    ```

3. Copie um `extension.vsixmanifest` existente e edite-o com um editor de XML. Altere a ID, o nome e os nós de conteúdo.

    - Você pode encontrar um exemplo de `extension.vsixmanifest` neste diretório:

         *unidade* **: \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles**

    - O nó de conteúdo deve ser assim:

        ```
        <Content>
          <CustomExtension Type="Microsoft.VisualStudio.UmlProfile"
          >YourProfile.Profile</CustomExtension>
        </Content>
        ```

4. Compacte os três arquivos em um arquivo compactado.

     No Windows Explorer, selecione os três arquivos, clique com o botão direito do mouse, aponte para **Enviar para**e clique em **pasta compactada (zipada)** .

5. Renomeie o arquivo zipado e altere sua extensão de nome de arquivo de `.zip` para `.vsix`.

6. Para instalar o perfil em qualquer computador com as edições apropriadas do Visual Studio, clique duas vezes no arquivo de `.vsix`.

#### <a name="to-install-a-uml-profile-from-a-visual-studio-extension"></a>Para instalar um perfil UML de uma extensão do Visual Studio

1. Clique duas vezes no arquivo `.vsix` no Windows Explorer ou abra-o no Visual Studio.

2. Clique em **instalar** na caixa de diálogo que aparece.

3. Para desinstalar ou desabilitar temporariamente a extensão, abra **extensões e atualizações** no menu **ferramentas** .

## <a name="Localized"></a>Como definir perfis localizados
 Você pode definir perfis diferentes para culturas ou idiomas diferentes e empacotá-los todos na mesma extensão. Quando um usuário carregar sua extensão, ele verá o perfil que você definiu para sua cultura.

 Você sempre deve fornecer um perfil padrão. Se você não tiver definido um perfil para a cultura do usuário, ele verá o perfil padrão.

#### <a name="to-define-a-localized-profile"></a>Para definir um perfil localizado

1. Crie um perfil conforme descrito nas seções anteriores[como definir um perfil](#DefineProfile) e [como adicionar um perfil a uma extensão do Visual Studio](#AddProfile). Esse é o perfil padrão e será usado em qualquer instalação para a qual você não forneça um perfil localizado.

2. Adicione um novo diretório no mesmo diretório que o seu arquivo de perfil padrão.

    > [!NOTE]
    > Se você estiver criando a extensão usando um projeto de extensão do Visual Studio, use Gerenciador de Soluções para adicionar uma nova pasta ao projeto.

3. Altere o nome do novo diretório para o código ISO curto para a cultura localizada, como `bg` para búlgaro ou `fr` para francês. Você deve usar um código de cultura neutro, normalmente duas letras, não uma cultura específica, como `fr-CA`. Para obter mais informações sobre códigos de cultura, consulte o [método CultureInfo. Getculturals](http://go.microsoft.com/fwlink/?LinkId=160782), que fornece uma lista completa de códigos de cultura.

4. Adicione uma cópia do seu perfil padrão ao novo diretório. Não altere seu nome de arquivo.

     Um exemplo de pasta de extensão [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], antes de ser compilado ou compactado em um arquivo de `.vsix`, conterá as seguintes pastas e arquivos:

     `extension.vsixmanifest`

     `MyProfile.profile`

     `fr\MyProfile.profile`

     `de\MyProfile.profile`

    > [!NOTE]
    > Você não deve inserir em `extension.vsixmanifest` uma referência às versões localizadas dos perfis. Os arquivos de perfil copiados devem ter o mesmo nome que o perfil na pasta pai.

5. Edite a nova cópia do perfil, convertendo para o idioma de destino todas as partes que serão visíveis para o usuário, como os atributos de `displayName`.

6. Você pode criar pastas de cultura adicionais e perfis localizados para quantas culturas desejar.

7. Crie a extensão do Visual Studio, seja criando o projeto de extensão ou compactando todos os arquivos, conforme descrito nas seções anteriores.

## <a name="Schema"></a>A estrutura de um perfil
 O arquivo XSD para perfis UML pode ser encontrado no exemplo a seguir: [Configurando estereótipos e perfis XSD](http://go.microsoft.com/fwlink/?LinkID=213811). Para ajudá-lo a editar os arquivos de perfil, instale o arquivo de `.xsd` em:

 **%ProgramFiles%\Microsoft Visual Studio [versão] \Xml\Schemas**

 Esta seção usa o C# perfil como exemplo. A definição completa do perfil pode ser vista em:

 *unidade* **: \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles\CSharp.Profile**

 As primeiras partes desse caminho podem ser diferentes na sua instalação.

 Para obter mais informações sobre o perfil do .NET, consulte [estereótipos padrão para modelos UML](../modeling/standard-stereotypes-for-uml-models.md).

### <a name="main-sections-of-the-uml-profile-definition"></a>Seções principais da definição do perfil UML
 Cada perfil contém o seguinte conteúdo:

```
<?xml version="1.0" encoding="utf-8"?>
<profile dslVersion="1.0.0.0"
       name="CSharpProfile" displayName="C# Profile"
       xmlns="http://schemas.microsoft.com/UML2.1.2/ProfileDefinition">
  <stereotypes>...</stereotypes>
  <metaclasses>...</metaclasses>
  <propertyTypes>...</propertyTypes>
</profile>
```

> [!NOTE]
> O atributo chamado `name` não deve conter espaços ou pontuação. O atributo `displayName`, que aparece na interface do usuário, deve ser uma cadeia de caracteres XML válida.

 Cada perfil contém três seções principais. Na ordem inversa, eles são os seguintes:

- `<propertyTypes>`-uma lista de tipos que são usados para propriedades definidas na seção estereótipos.

- `<metaclasses>`-uma lista de tipos de elementos de modelo aos quais os estereótipos neste perfil se aplicam, como IClass, IInterface, IOperation, IDependency.

- `<stereotypes>`-as definições de estereótipo. Cada definição inclui os nomes e tipos de propriedades que são adicionados ao elemento de modelo de destino.

#### <a name="property-types"></a>Tipos de propriedade
 A seção `<propertyTypes>` declara uma lista de tipos que são usados para propriedades na seção `<stereotypes>`. Há dois tipos de tipos de propriedade: external e Enumeration.

 Um tipo externo declara o nome totalmente qualificado de um tipo .NET padrão:

```
<externalType name="System.String" />
```

 Um tipo de enumeração define um conjunto de valores literais:

```
<enumerationType name="PackageVisibility">
  <enumerationLiterals>
    <enumerationLiteral name="internal" displayName="internal"  />
    <enumerationLiteral name="protectedinternal" displayName="protected internal" />
  </enumerationLiterals>
</enumerationType>
```

#### <a name="metaclasses"></a>Metaclasses
 A seção `<metaclasses>` é uma lista de tipos de elementos de modelo para os quais os estereótipos neste perfil podem ser definidos:

```
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IClass" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Classes.IInterface" />
<metaclass
      name="Microsoft.VisualStudio.Uml.Components.IComponent" />
```

 Para obter a lista completa de elementos de modelo e tipos de relação que você pode usar como metaclasses, consulte [tipos de elemento de modelo](#Elements).

#### <a name="stereotype-definition"></a>Definição de estereótipo
 A seção `<stereotypes>` contém uma ou mais definições de estereótipo:

```
<stereotype name="CSharpClass" displayName="C# Class"> ...
```

 Cada estereótipo lista um ou mais elementos de modelo ou tipos de relação aos quais ele pode ser aplicado. Você pode atribuir o nome de um tipo base, para incluir todos os seus tipos derivados. Por exemplo, se você especificar `Microsoft.VisualStudio.Uml.Classes.IType`, o estereótipo poderá ser aplicado a `IClass`, `IInterface`, `IEnumeration` e vários outros tipos de elemento.

```
<metaclasses>
  <metaclassMoniker name=
   "/CSharpProfile/Microsoft.VisualStudio.Uml.Classes.IClass" />
</metaclasses>
```

 O atributo `name` de `metaclassMoniker` é um link para um elemento na seção `<metaClasses>`.

> [!NOTE]
> O nome do moniker deve começar com `/yourProfileName/`, em que `yourProfileName` é definido no atributo `name` do perfil ("CSharpProfile" neste exemplo). O moniker termina com o nome de uma das entradas na seção metaclasses.

 Cada estereótipo pode listar zero ou mais propriedades que ele adiciona a qualquer elemento de modelo ao qual ele é aplicado. O `<propertyType>` contém um link para um dos tipos definidos na seção `<propertyTypes>`. O link deve ser um `<externalTypeMoniker>` para referir-se a um `<externalType>,` ou um `<enumerationTypeMoniker>` para se referir a um `<enumerationType>`. Novamente, o link começa com o nome do seu perfil.

```
  <properties>
    <property name="IsStatic"
            displayName="Is Static" defaultValue="false">
      <propertyType>
<externalTypeMoniker
               name="/CSharpProfile/System.Boolean" />
      </propertyType>
    </property>
    <property name="PackageVisibility"
              displayName="Package Visibility"
              defaultValue="internal">
      <propertyType>
        <enumerationTypeMoniker
              name="/CSharpProfile/PackageVisibility"/>
      </propertyType>
    </property>
  </properties>
</stereotype>
```

## <a name="Elements"></a>Tipos de elementos de modelo
 O conjunto de tipos para os quais você pode definir estereótipos está listado em [tipos de elementos de modelo UML](../modeling/uml-model-element-types.md).

## <a name="troubleshooting"></a>Solução de problemas
 Meus estereótipos não aparecem nos meus modelos UML.
Você precisa selecionar seu perfil em um pacote ou modelo. Os estereótipos serão exibidos em elementos dentro do pacote ou modelo. Para obter mais informações, consulte [Adicionar estereótipos a elementos de modelo UML](../modeling/add-stereotypes-to-uml-model-elements.md).

 O seguinte erro aparece quando abro um modelo UML: **VS1707: os seguintes perfis não podem ser carregados porque ocorreu um erro de serialização: MyProfile. Profile**
1. Verifique se a sintaxe XML básica do. Profile está correta.

2. Verifique se cada nome do moniker está no formato/profileName/nodeName. O ProfileName é o valor do atributo Name no nó raiz do perfil. NodeName é o valor do atributo Name de uma metaclasse, externalType ou EnumerationType.

3. Verifique se a sintaxe é descrita aqui e, conforme demonstrado em _unidade_ **: \Program Files\Microsoft Visual Studio [Version] \Common7\IDE\Extensions\Microsoft\Architecture Tools\UmlProfiles \\** .

4. Desinstale a extensão com falha. No menu **ferramentas** , clique em **extensões e atualizações**.

   - Se a extensão não aparecer, consulte o próximo item.

5. Recompile o arquivo VSIX e abra-o no Windows Explorer para reinstalá-lo. Reinicie o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   A extensão não aparece no Gerenciador de extensões, mas quando você tenta reinstalá-la, a seguinte mensagem é exibida: **a extensão já está instalada em todos os produtos aplicáveis.**
   1. Remova o arquivo de extensão de uma subpasta de *LocalAppData*\Microsoft\VisualStudio \\ [Version] \Extensions\

   - Para ver *LocalAppData*, você deve definir mostrar arquivos ocultos e pastas na guia Exibir das opções de pasta do Windows Explorer.

   - *LocalAppData* normalmente está em C:\Users \\*nome de usuário*\AppData\Local\

6. Reinicie o [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="see-also"></a>Consulte também
 [Adicionar estereótipos a elementos de modelo UML](../modeling/add-stereotypes-to-uml-model-elements.md) [Personalize seu modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [padrões de estereótipos para modelos UML](../modeling/standard-stereotypes-for-uml-models.md) [exemplo: colorir elementos UML por](http://go.microsoft.com/fwlink/?LinkID=213841) [amostra de estereótipo: definindo estereótipos, perfis XSD](http://go.microsoft.com/fwlink/?LinkID=213811)
