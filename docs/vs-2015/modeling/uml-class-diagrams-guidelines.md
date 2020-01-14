---
title: 'Diagramas de classe UML: diretrizes | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.logicalclassdiagram.overrideoperationsdialog
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: 94dbfd55-b300-4b49-9049-0831ed849486
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f4fd6eed634da3aea956cddca8d2e1ff6220a94
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850196"
---
# <a name="uml-class-diagrams-guidelines"></a>Diagramas de classe UML: diretrizes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, você pode usar um *diagrama de classe UML* para descrever tipos de dados e suas relações separadamente de sua implementação. O diagrama é usado para enfocar os aspectos lógicos das classes, em vez de sua implementação.

 Para criar um diagrama de classe UML, no menu **arquitetura** , escolha **novo diagrama UML ou diagrama de camada**.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Este tópico é sobre diagramas de classe UML. Há outro tipo de diagrama de classes, que é possível criar e usar para visualizar o código do programa. Consulte [criando e exibindo classes e tipos](https://msdn.microsoft.com/library/ab7aty24.aspx).

## <a name="Using"></a>Usando diagramas de classe UML
 É possível usar um diagrama de classes UML com várias finalidades:

- Para fornecer uma descrição independente de implementação dos tipos usados em um sistema e passados entre seus componentes.

     Por exemplo, o tipo Meal Order pode ser implementado no código do .NET na camada comercial, no XML nas interfaces entre componentes, no SQL no banco de dados e no HTML na interface do usuário. Embora essas implementações sejam diferentes em detalhes, a relação entre um Meal Order e outros tipos como, por exemplo, Menu e Payment, é sempre a mesma. O diagrama de classes UML possibilita discutir essas relações separadamente das implementações.

- Para esclarecer o glossário de termos usado na comunicação entre o aplicativo e seus usuários e nas descrições das necessidades dos usuários. Consulte [requisitos de usuário de modelo](../modeling/model-user-requirements.md).

     Por exemplo, leve em consideração as histórias do usuário, os casos de uso ou outras descrições dos requisitos de um aplicativo de um restaurante. Em uma descrição assim, você encontraria termos como Menu, Order, Meal, Price, Payment etc. Você poderia chamar um diagrama de classes UML que define as relações entre esses termos. Isso reduzirá o risco de inconsistências nas descrições dos requisitos, na interface do usuário e nos documentos de ajuda.

### <a name="relationship-to-other-diagrams"></a>Relação com Outros Diagramas
 Um diagrama de classes UML costuma ser desenhado com outros diagramas de modelagem para fornecer descrições dos tipos que usam. Em cada caso, a representação física dos tipos não é implícita de alguns dos diagramas.

 Diagrama de atividade

 Tipo de dados passado por um nó do objeto.

 Tipos de pinos de entrada e saída e dos nós de parâmetro de atividade.

 Consulte [diagramas de atividade UML: diretrizes](../modeling/uml-activity-diagrams-guidelines.md).

 Diagrama de sequência

 Tipos de parâmetros e valores de retorno das mensagens.

 Tipos de linhas da vida. A classe de uma linha da vida deve incluir operações de todas as mensagens que pode receber.

 Consulte [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md).

 Diagrama de componente

 Interfaces de componente, listando suas operações.

 Consulte [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md).

 Diagrama de caso de uso

 Tipos mencionados em descrições das meta e das etapas de um caso de uso.

 Consulte [diagramas de caso de uso UML: diretrizes](../modeling/uml-use-case-diagrams-guidelines.md).

## <a name="BasicSteps"></a>Etapas básicas para desenhar diagramas de classe
 Para obter informações de referência sobre os elementos em diagramas de classe UML, consulte [diagramas de classe UML: Reference](../modeling/uml-class-diagrams-reference.md).

> [!NOTE]
> As etapas detalhadas para a criação de qualquer um dos diagramas de modelagem são descritas em [editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md).

#### <a name="to-create-a-uml-class-diagram"></a>Para criar um diagrama de classes UML

1. No menu **arquitetura** , escolha **novo UML ou diagrama de camada**.

2. Em **modelos**, escolha **diagrama de classe UML**.

3. Nomeie o diagrama.

4. Em **Adicionar ao projeto de modelagem**, selecione um projeto de modelagem existente em sua solução ou **crie um novo projeto de modelagem**e, em seguida, escolha **OK**.

     Um novo diagrama de classe é exibido com a caixa de ferramentas de **diagrama do UMLClass** . A Caixa de Ferramentas contém os elementos e as relações obrigatórios.

#### <a name="to-draw-a-uml-class-diagram"></a>Para desenhar um Diagrama de Classe UML

1. Para criar um tipo, escolha a ferramenta **classe**, **interface** ou **Enumeração** na caixa de ferramentas e, em seguida, clique em uma parte em branco do diagrama. (Se você não conseguir ver a Caixa de Ferramentas, pressione CTRL+ALT+X.)

2. Para adicionar atributos ou operações aos tipos, ou literais a uma enumeração, escolha o cabeçalho **atributos**, **operações** ou **literais** no tipo e pressione Enter.

     É possível gravar uma assinatura como `f(x:Boolean):Integer`. Consulte [atributos e operações](#AttributesAndOperations).

     Para adicionar vários itens rapidamente, pressione ENTER duas vezes ao final de cada item. É possível usar as teclas de direção para mover a lista para cima e para baixo.

3. Para expandir ou recolher um tipo, escolha o ícone de divisa no canto superior esquerdo. Você também pode expandir e recolher a seção **atributos** e **operações** de uma classe ou interface.

4. Para desenhar associações, herança ou links de dependência entre os tipos, clique na ferramenta apropriada, no tipo de origem e no tipo de destino.

5. Para criar tipos em um pacote, crie um pacote usando a ferramenta de **pacote** e, em seguida, crie novos tipos e pacotes no pacote. Também é possível usar o comando copiar para copiar tipos e colá-los em um pacote.

6. Cada diagrama é uma exibição em um modelo compartilhado entre outros diagramas no mesmo projeto. Para ver um modo de exibição de árvore do modelo completo, escolha **Exibir**, **outras janelas**, **Gerenciador de modelos UML**.

## <a name="UsingTypes"></a>Usando classes, interfaces e enumerações
 Existem três tipos padrão de classificadores disponíveis na caixa de ferramentas. Eles são chamados de *tipos* em todo este documento.

 ![Uma classe, uma enumeração e uma interface](../modeling/media/uml-classguidetypes.png "UML_ClassGuideTypes")

- Use **classes** (1) para representar dados ou tipos de objeto para a maioria das finalidades.

- Use **interfaces** (2) em um contexto onde você precisa diferenciar entre interfaces puras e classes concretas que têm implementações internas. Essa diferença é útil quando a finalidade do diagrama é descrever uma implementação de software. Isso é menos útil quando você está modelando dados passivos ou definindo conceitos usados para descrever os requisitos de usuário.

- Use uma **Enumeração** (3) para representar um tipo que tenha um número limitado de valores literais, por exemplo `Stop` e `Go`.

  - Adicione os valores literais à enumeração. Dê a cada um nome separado.

  - Também é possível fornecer um valor numérico para cada valor literal, se você quiser. Abra o menu de atalho para o literal na enumeração, escolha **Propriedades**e digite um número no campo **valor** na janela **Propriedades** .

  Dê a cada tipo um nome exclusivo.

### <a name="getting-types-from-other-diagrams"></a>Obtendo Tipos de Outros Diagramas
 Também é possível fazer tipos de outro diagrama serem exibidos no diagrama de classes UML.

 Diagrama de Classes UML

 É possível fazer uma classe ser exibida em mais de um diagrama de classes UML. Quando você tiver criado uma classe em um diagrama, arraste a classe do **Gerenciador de modelos UML** para outro diagrama.

 Isso será útil se você quiser que cada diagrama enfoque um grupo específico de relações.

 Por exemplo, você poderia mostrar as associações entre uma Meal Order e o Menu de um restaurante em um diagrama, e as associações entre Meal Order e Payment em outro diagrama.

 Diagrama do componente

 Se você tiver definido interfaces nos componentes em um diagrama de componente, poderá arrastar uma interface do **Gerenciador de modelos UML** para o diagrama de classe. No diagrama da classe, é possível definir os métodos incluídos na interface.

 Consulte [diagramas de componentes UML: diretrizes](../modeling/uml-component-diagrams-guidelines.md).

 Diagrama de Sequência UML

 Você pode criar classes e interfaces de linhas de vida em um diagrama de sequência e, em seguida, arrastar a classe do **Gerenciador de modelos UML** para um diagrama de classes UML. Cada linha da vida em um diagrama de sequência representa uma instância de um objeto, componente ou ator.

 Para criar uma classe de uma linha de vida, abra o menu de atalho para a linha da vida e escolha **criar classe** ou **criar interface**. Consulte [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md).

## <a name="AttributesAndOperations"></a>Atributos e operações
 Um atributo (4) é um valor nomeado que toda instância de um tipo pode ter. O acesso a um atributo não altera o estado da instância.

 Uma operação (5) é um método ou uma função que instâncias do tipo podem realizar. Ele pode retornar um valor. Se sua propriedade **IsQuery** for true, ela não poderá alterar o estado da instância.

 Para adicionar um atributo ou uma operação a um tipo, abra o menu de atalho para o tipo, escolha **Adicionar**e, em seguida, escolha **atributo** ou **operação**.

 Para ver suas propriedades, abra o menu de atalho para o atributo ou a operação e escolha **Propriedades**. As propriedades aparecem na janela **Propriedades** .

 Para ver as propriedades dos parâmetros de uma operação, escolha <strong>[...]</strong> na propriedade **Parameters** . Uma nova caixa de diálogo de propriedades é exibida.

 Para obter informações detalhadas sobre todas as propriedades que é possível definir, consulte:

- [Propriedades de atributos em diagramas de classe UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Propriedades de operações em diagramas de classe UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

### <a name="types-of-attributes-and-operations"></a>Tipos de Atributos e Operações
 Cada *tipo* de um atributo ou operação, e cada tipo de parâmetro, pode ser um dos seguintes:

- **(nenhum)** – você pode deixar um tipo não especificado na assinatura omitindo os dois-pontos precedentes (`:`).

- Um dos tipos primitivos padrão: **booliano**, **inteiro**, **cadeia de caracteres**.

- Um tipo definido no modelo.

- Um valor com parâmetros de um tipo de modelo, modelo gravado\<> de parâmetro. Consulte [tipos de modelo](#Templates).

  Também é possível gravar o nome de um tipo que você ainda não definiu no modelo. O nome será listado sob **tipos não especificados** no Gerenciador de modelos UML.

> [!NOTE]
> Se você definir depois uma classe ou uma interface desse nome no modelo, os atributos e as operações posteriores continuarão fazendo referência ao elemento em Tipos Não Especificados. Se quiser alterá-los para fazer referência à nova classe, você deverá visitar cada atributo ou operação e redefinir o tipo, selecionando a nova classe no menu suspenso.

#### <a name="multiple-types"></a>Vários Tipos
 É possível definir uma multiplicidade de qualquer atributo, operação ou tipo de parâmetro.

 Os valores permitidos são os seguintes:

 `[1]`

 Um valor do tipo indicado. Este é o padrão.

 `[0..1]`

 **NULL** ou um valor do tipo fornecido.

 `[*]`

 Uma coleção de qualquer número de instâncias do tipo indicado.

 `[1..*]`

 Uma coleção de pelo menos uma instância do tipo indicado.

 `[n..m]`

 Uma coleção de instâncias entre `n` e `m` do tipo indicado.

 Se a multiplicidade for maior que 1, também será possível definir essas propriedades:

- **Isordened** -se true, a coleção terá uma ordem definida.

- **IsUnique** -se for true, não haverá valores duplicados na coleção.

### <a name="visibility"></a>Visibilidade
 *Visibility* indica se o atributo ou a operação pode ser acessada fora da definição de classe. Os valores permitidos são os seguintes:

 **Público**

 **+**

 Acessível com base em todos os outros tipos.

 **Privado**

 **-**

 Acessível somente à definição interna desse tipo.

 **Pacote**

 **~**

 Acessível somente dentro do pacote que contém esse tipo e em alguns pacotes que o importam explicitamente. Consulte [definindo namespaces e pacotes](#Packages).

 **Protegido**

 **#**

 Acessível apenas a esse tipo e tipos herdados dele. Consulte [herança](#Inheritance).

### <a name="setting-the-signature-of-an-attribute-or-an-operation"></a>Definindo a Assinatura de um Atributo ou de uma Operação
 A assinatura de um atributo ou de uma operação é uma coleção de propriedades que inclui sua visibilidade, seu nome, seus parâmetros (para operações) e seu tipo.

 É possível gravar uma assinatura diretamente no diagrama. Clique no atributo ou na operação para selecioná-lo e, em seguida, clique nele novamente.

 Grave a assinatura na forma:

```
visibility attribute-name : Type
```

 \- ou -

```
visibility operation-name (parameter1 : Type1, ...) : Type
```

 Por exemplo:

```
+ AddItem (item : MenuItem, quantity : Integer) : Boolean
```

 Use a forma abreviada da visibilidade. O valor padrão é `+` (público).

 Cada tipo pode ser um tipo definido no modelo, tipos padrão como Integer ou String, ou o nome de um novo tipo ainda não definido.

> [!NOTE]
> Se você gravar um nome sem um tipo em uma lista de parâmetros, ele indicará o nome do parâmetro, em vez do tipo. Neste exemplo, MenuItem e Integer se tornam os nomes dos dois parâmetros com tipos não especificados:
>
> `AddItem(MenuItem, Integer) /* parameter names, not types! */`

 Para definir a multiplicidade de um tipo em uma assinatura, grave a multiplicidade entre colchetes depois do nome do tipo, por exemplo:

```
+ AddItems (items : MenuItem [1..*])
+ MenuContent : MenuItem [*]
```

 Se o atributo ou a operação for estática, seu nome será exibido sublinhado na assinatura. Se ele for abstrato, o nome será exibido na fonte em itálico.

 No entanto, você só pode definir as propriedades **is static** e **abstract** na janela **Properties** .

#### <a name="full-signature"></a>Assinatura Completa
 Quando você edita a assinatura de um atributo ou de uma operação, algumas propriedades adicionais podem ser exibidas ao final da linha e depois de cada parâmetro. Eles são exibidos entre chaves {…}. É possível editar ou adicionar essas propriedades. Por exemplo:

```
+ AddItems (items: MenuItem [1..*] {unique, ordered})
+ GetItems (filter: String) : MenuItem [*] {ordered, query}
```

 Estas são as seguintes propriedades:

 `unique`

 **É Exclusivo**

 Não há valores duplicados na coleção. Aplica-se a tipos com multiplicidade maior que 1.

 `ordered`

 **É ordenado**

 A coleção é uma sequência. Se for falso, não haverá um primeiro item definitivo. Aplica-se a tipos com multiplicidade maior que 1.

 `query`

 **É consulta**

 A operação não altera o estado da instância. Aplica-se apenas a operações.

 `/`

 **É derivado**

 O atributo é computado com base em valores de outros atributos ou associações.

 "/" é exibido antes do nome de um atributo. Por exemplo:

```
/TotalPrice: Integer
```

 Normalmente, a assinatura completa é exibida no diagrama apenas durante a edição. Quando você terminar a edição, as propriedades adicionais permanecerão ocultas. Se você quiser ver a assinatura completa o tempo todo, abra o menu de atalho para o tipo e escolha **Mostrar assinatura completa**.

## <a name="Associations"></a>Desenho e uso de associações
 Use uma associação para representar qualquer tipo de um vínculo entre dois elementos, independentemente de como o vínculo é implementado no software. Por exemplo, você poderia usar uma associação para representar um ponteiro no C#, uma relação em um banco de dados ou uma referência cruzada de uma parte de um arquivo XML para outra. Ela pode representar uma associação entre objetos no mundo real, como a terra e o sol. A associação não informa como o link é representado, somente as informações existentes.

### <a name="properties-of-an-association"></a>Propriedades de uma Associação
 Depois que você criar uma associação, defina suas propriedades. Abra o menu de atalho para a associação e, em seguida, escolha **Propriedades**.

 Além das propriedades da associação como um todo, cada *função*, ou seja, cada extremidade da associação, tem algumas propriedades próprias. Para exibi-los, expanda a **primeira função** e as propriedades da **segunda função** .

 Algumas propriedades de cada função estão diretamente visíveis no diagrama. Elas são as seguintes:

- Nome da função. Ela é exibida na extremidade apropriada de associação no diagrama. Você pode defini-lo no diagrama ou na janela **Propriedades** .

- **Multiplicidade**, cujo padrão é **1**. Ela também é exibida no diagrama próximo à extremidade apropriada da associação.

- **Agregação**. Ela é exibida como uma forma de diamante ao final do conector. É possível usá-la para indicar que as instâncias na função de agregação têm ou contêm instâncias das outras.

- **É navegável**. Se for verdadeiro apenas para uma função, uma seta será exibida na direção navegável. É possível usá-la para indicar a navegabilidade de links e relações do base de dados do software.

  Para obter os detalhes completos dessas e outras propriedades, consulte [Propriedades de associações em diagramas de classe UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).

### <a name="navigability"></a>Navegabilidade
 Quando você desenha uma associação, ela tem uma seta em uma extremidade, o que significa que a associação é navegável nessa direção. Isso será útil se o diagrama da classe representar classes de software e as associações representarem ponteiros ou referências. Mas quando você usa um diagrama de classes para representar entidades e relações ou conceitos de negócio, ela é menos relevante representar navegabilidade. Nesse caso, você talvez prefira desenhar associações sem setas. Isso pode ser feito definindo a propriedade **navegável** em ambas as extremidades da associação como true.

### <a name="attributes-and-associations"></a>Atributos e Associações
 Uma associação é uma maneira pictórica de mostrar um atributo. Por exemplo, em vez de criar uma classe Restaurant com um atributo do tipo Menu, é possível desenhar uma associação de Restaurant até Menu.

 Cada nome do atributo se torna um nome da função. Ele é exibido na extremidade oposta da associação em relação ao tipo proprietário. Observe, por exemplo, `myMenu` na ilustração.

 Normalmente, é melhor usar atributos apenas para tipos que você não desenharia no diagrama, como tipos primitivos.

 ![Associação e atributos equivalentes](../modeling/media/uml-classguideattrib.png "UML_ClassGuideAttrib")

## <a name="Inheritance"></a> Herança
 Use a ferramenta de **herança** para criar as seguintes relações:

- Uma relação de *generalização* entre um tipo especializado e um tipo geral

   \- ou -

- Uma relação de *realização* entre uma classe e uma interface que ela implementa.

  Não é possível criar loop em relações de herança.

### <a name="generalization"></a>Generalização
 A generalização significa que a especialização ou o tipo derivado herda atributos, operações e associações do tipo geral ou base.

 O tipo geral é exibido ao final da seta da relação.

 As operações e os atributos herdados não costumam ser mostrados nos tipos de especialização. Mas é possível adicionar operações herdadas à lista das operações do tipo de especialização. Isso será útil se você quiser substituir qualquer uma das propriedades de uma operação no tipo de especialização, ou se quiser indicar que o código de implementação deve fazer isso.

##### <a name="to-override-an-operations-definition-in-a-specializing-type"></a>Para substituir a definição de uma operação em um tipo de especialização

1. Clique na relação de generalização.

    Ela é exibida realçada, e uma marca Ação é exibida próxima dela.

2. Clique na marca de ação e, em seguida, clique em **operações de substituição**.

    A caixa de diálogo **operações de substituição** é exibida.

3. Selecione as operações que você deseja que apareçam no tipo de especialização e clique em **OK**.

   As operações selecionadas agora são exibidas no tipo de especialização.

### <a name="realization"></a>Realização
 Realização significa que uma classe implementa os atributos e as operações especificados pela interface. A interface está na extremidade da seta do conector.

 Quando você cria um conector de realização, as operações da interface são replicadas automaticamente na classe de realização. Se você adicionar novas operações a uma interface, elas serão replicadas em suas classes de realização.

 Depois de criar uma relação de realização, você poderá convertê-la na notação pirulito. Clique com o botão direito do mouse na relação e escolha **mostrar como pirulito**.

 Isso permite mostrar as interfaces que uma classe implementa, sem desorganizar os diagramas de classes com links de realização. Também é possível mostrar a interface e as classes que fazem isso em diagramas separados.

 ![Realização mostrada com conector e pirulito](../modeling/media/uml-classguiderealize.png "UML_ClassGuideRealize")

## <a name="Templates"></a>Tipos de modelo
 É possível definir um tipo ou um modelo genérico que pode ser parametrizado por outros tipos ou valores.

 Por exemplo, é possível criar um Dicionário genérico parametrizado por chave e tipos de valor:

 ![Classe de modelo com dois parâmetros](../modeling/media/uml-classguidetemplate1.png "UML_ClassGuideTemplate1")

#### <a name="to-create-a-template-type"></a>Para criar um tipo de modelo

1. Crie uma classe ou uma interface. Ele se tornará o tipo de modelo. Nomeie-o de acordo, por exemplo, `Dictionary`.

2. Abra o menu de atalho para o novo tipo e, em seguida, escolha **Propriedades**.

3. Na janela **Propriedades** , clique em **[...]** no campo **parâmetros de modelo** .

    A caixa de diálogo **Editor de coleção de parâmetros de modelo** é exibida.

4. Escolha **Adicionar**.

5. Defina a propriedade de nome como um nome de parâmetro para o tipo de modelo, por exemplo, `Key`.

6. Definir **tipo de parâmetro**. O padrão é **Class**.

7. Se você quiser que o parâmetro aceite apenas classes derivadas de uma classe base específica, defina o **valor restrito** para a classe base que você deseja.

8. Adicione quantos parâmetros forem necessários e escolha **OK**.

9. Adicione atributos e operações ao tipo de modelo como você faria para outras classes.

     Você pode usar parâmetros cujo tipo é **Class**, **interface** ou **Enumeration** na definição de atributos e operações. Por exemplo, usando classes `Key` e `Value`, você poderia definir essa operação em `Dictionary`:

     `Get(k : Key) : Value`

     Você pode usar um parâmetro cujo tipo é **inteiro** como um limite em uma multiplicidade. Por exemplo, um inteiro de parâmetro max poderia ser usado para definir a multiplicidade de um atributo como `[0..max]`.

   Quando tiver criado tipos de modelo, você poderá usá-los para definir associações do modelo:

   ![Uma classe associada do modelo de dicionário](../modeling/media/uml-classguidetemplate2.png "UML_ClassGuideTemplate2")

#### <a name="to-use-a-template-type"></a>Para usar um tipo de modelo

1. Crie um novo tipo, por exemplo, `AddressTable`.

2. Abra o menu de atalho para o novo tipo e, em seguida, escolha **Propriedades**.

3. Na propriedade **Associação de modelo** , selecione o tipo de modelo, por exemplo `Dictionary`, na lista suspensa.

4. Expanda a propriedade de **Associação de modelo** .

     Uma linha é exibida para cada parâmetro do tipo de modelo.

5. Defina cada parâmetro com um valor apropriado. Por exemplo, defina o parâmetro `Key` como uma classe chamada `Name`.

## <a name="Packages"></a>Compacta
 É possível exibir pacotes em um diagrama de classes UML. Um pacote é um contêiner de outros elementos do modelo. É possível criar qualquer elemento dentro de um pacote. No diagrama, os elementos dentro do pacote serão movidos quando você mover o pacote.

 É possível usar o controle expandir/recolher para ocultar ou mostrar o conteúdo do pacote.

 Consulte [definir pacotes e namespaces](../modeling/define-packages-and-namespaces.md).

## <a name="generating"></a>Gerando código de diagramas de classe UML
 Para iniciar a implementação das classes em um diagrama de classes UML, é possível gerar o código do C# ou personalizar os modelos para a geração de códigos. Para iniciar a geração de códigos usando os modelos fornecidos do C#:

- Abra o menu de atalho do diagrama ou de um elemento, escolha **gerar código**e, em seguida, defina as propriedades necessárias.

     Para obter mais informações sobre como definir essas propriedades e personalizar os modelos fornecidos, consulte [gerar código de diagramas de classe UML](../modeling/generate-code-from-uml-class-diagrams.md).

## <a name="see-also"></a>Veja também
 [Editar modelos UML e](../modeling/edit-uml-models-and-diagrams.md) diagramas [diagramas de classes UML:](../modeling/uml-class-diagrams-reference.md) [requisitos de usuário do modelo](../modeling/model-user-requirements.md) de referência [diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md) [diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md) diagramas de [caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md) [diagramas de componentes UML: referência](../modeling/uml-component-diagrams-reference.md)
