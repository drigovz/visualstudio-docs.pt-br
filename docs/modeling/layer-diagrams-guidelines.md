---
title: 'Diagramas de dependência: diretrizes'
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39da24dd0d8b7372c63609124ee0b9427fccb03d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661500"
---
# <a name="dependency-diagrams-guidelines"></a>Diagramas de dependência: diretrizes

Descreva a arquitetura do aplicativo em um alto nível criando *diagramas de dependência* no Visual Studio. Certifique-se de que seu código permaneça consistente com esse design validando seu código com um diagrama de dependência. Você também pode incluir a validação de camada em seu processo de compilação. Veja [vídeo do Channel 9: projete e valide sua arquitetura usando diagramas de dependência](http://go.microsoft.com/fwlink/?LinkID=252073).

Para ver quais edições do Visual Studio oferecem suporte a esse recurso, consulte [suporte de edição para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Há suporte para diagramas de dependência para projetos do .NET Core a partir do Visual Studio 2019 versão 16,2.

## <a name="what-is-a-dependency-diagram"></a>O que é um diagrama de dependência?

Como um diagrama de arquitetura tradicional, um diagrama de dependência identifica os principais componentes ou unidades funcionais do design e suas interdependências. Cada nó no diagrama, chamado de *camada*, representa um grupo lógico de namespaces, projetos ou outros artefatos. Você pode desenhar as dependências que devem existir em seu design. Ao contrário de um diagrama de arquitetura tradicional, você pode verificar se as dependências reais no código-fonte estão em conformidade com as dependências pretendidas que você especificou. Ao tornar a validação parte de uma compilação regular em [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], você pode garantir que o código do programa continue a aderir à arquitetura do sistema por meio de alterações futuras. Consulte [diagramas de dependência: referência](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Como criar ou atualizar seu aplicativo com diagramas de dependência

As etapas a seguir fornecem uma visão geral de como usar diagramas de dependência dentro do processo de desenvolvimento. As seções posteriores neste tópico descrevem mais detalhes sobre cada etapa. Se você estiver desenvolvendo um novo design, omita as etapas que se referem ao código existente.

> [!NOTE]
> Essas etapas aparecem em ordem aproximada. Você provavelmente desejará sobrepor as tarefas, reordená-las para atender à sua própria situação e revisitá-las no início de cada iteração em seu projeto.

1. [Crie um diagrama de dependência](#Create) para todo o aplicativo ou para uma camada dentro dele.

2. [Defina camadas para representar áreas funcionais primárias ou componentes](#CreateLayers) do seu aplicativo. Nomeie essas camadas de acordo com sua função, por exemplo, "apresentação" ou "serviços". Se você tiver uma solução do Visual Studio, poderá associar cada camada a uma coleção de *artefatos*, como projetos, namespaces, arquivos e assim por diante.

3. [Descubra as dependências existentes](#Generate) entre camadas.

4. [Edite as camadas e dependências](#EditArchitecture) para mostrar o design atualizado que você deseja que o código reflita.

5. [Projete novas áreas de seu aplicativo](#NewAreas) criando camadas para representar os blocos ou componentes de arquitetura principal e definir dependências para mostrar como cada camada usa os outros.

6. [Edite o layout e a aparência do diagrama](#EditLayout) para ajudá-lo a discuti-lo com colegas.

7. [Valide o código em relação ao diagrama de dependência](#Validate) para realçar os conflitos entre o código e a arquitetura que você precisa.

8. [Atualize o código para estar de acordo com sua nova arquitetura](#UpdateCode). Desenvolva e refatore o código de forma iterativa até que a validação não mostre nenhum conflito.

9. [Inclua a validação de camada no processo de compilação](#BuildValidation) para garantir que o código continue a aderir ao design.

## <a name="Create"></a>Criar um diagrama de dependência

Um diagrama de dependência deve ser criado dentro de um projeto de modelagem. Você pode adicionar um novo diagrama de dependência a um projeto de modelagem existente, criar um novo projeto de modelagem para o diagrama de dependência ou copiar um diagrama de dependência existente dentro do mesmo projeto de modelagem.

> [!IMPORTANT]
> Não adicione, arraste ou copie um diagrama de dependência existente de um projeto de modelagem para outro projeto de modelagem ou para outro local na solução. Um diagrama de dependência que é copiado dessa forma terá as mesmas referências que o diagrama original, mesmo se você modificar o diagrama. Isso impedirá que a validação de camada funcione corretamente e possa causar outros problemas, como elementos ausentes ou outros erros ao tentar abrir o diagrama.

Confira [criar diagramas de dependência do seu código](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a>Definir camadas para representar áreas funcionais ou componentes

Camadas representam grupos lógicos de *artefatos*, como projetos, arquivos de código, namespaces, classes e métodos. Você pode criar camadas de artefatos de C# projetos Visual e Visual Basic, ou pode anexar especificações ou planos a uma camada vinculando documentos, como arquivos do Word ou apresentações do PowerPoint. Cada camada aparece como um retângulo no diagrama e mostra o número de artefatos vinculados a ele. Uma camada pode conter camadas aninhadas que descrevem tarefas mais específicas.

Como uma diretriz geral, as camadas de nome de acordo com sua função, por exemplo, "apresentação" ou "serviços". Se os artefatos estiverem fortemente interdependentes, coloque-os na mesma camada. Se os artefatos puderem ser atualizados separadamente ou usados em aplicativos separados, coloque-os em camadas diferentes. Para saber mais sobre padrões de camadas, visite o site Patterns & Practices em [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Há certos tipos de artefatos que você pode vincular a camadas, mas que não dão suporte à validação em relação ao diagrama de dependência. Para ver se o artefato dá suporte à validação, abra o **Gerenciador de camadas** para examinar a propriedade de **validação de suporte** do link do artefato. Consulte [descobrir dependências existentes entre camadas](#Generate).

Ao atualizar um aplicativo desconhecido, você também pode criar mapas de código. Esses diagramas podem ajudá-lo a descobrir padrões e dependências enquanto explora o código. Use Gerenciador de Soluções para explorar namespaces e classes, que geralmente correspondem bem às camadas existentes. Atribua esses artefatos de código a camadas arrastando-os de Gerenciador de Soluções para diagramas de dependência. Você pode usar diagramas de dependência para ajudá-lo a atualizar o código e mantê-lo consistente com o design.

Consulte:

- [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)

- [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a>Descobrir dependências existentes entre camadas

Existirá uma dependência sempre que um artefato associado a uma camada tiver uma referência a um artefato associado a outra camada. Por exemplo, uma classe em uma camada declara uma variável que tem uma classe em outra camada. Você pode descobrir dependências existentes por meio da engenharia reversa.

> [!NOTE]
> As dependências não podem sofrer engenharia reversa para determinados tipos de artefatos. Por exemplo, nenhuma dependência sofrerá engenharia reversa de ou para uma camada vinculada a um arquivo de texto. Para ver quais artefatos têm dependências que você pode fazer engenharia reversa, clique com o botão direito do mouse em uma ou várias camadas e clique em **exibir links**. No **Gerenciador de camadas**, examine a coluna de **validação de suporte** . As dependências não serão criadas com engenharia reversa para artefatos para os quais essa coluna mostra **false**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Para fazer engenharia reversa de dependências existentes entre camadas

Selecione uma camada ou várias camadas, clique com o botão direito do mouse em uma camada selecionada e clique em **gerar dependências**.

Normalmente, você verá algumas dependências que não devem existir. É possível editar essas dependências para alinhá-las com o design desejado.

## <a name="EditArchitecture"></a>Editar camadas e dependências para mostrar o design pretendido

Para descrever as alterações que você planeja fazer no sistema ou na arquitetura pretendida, use as etapas a seguir para editar o diagrama de dependência. Você também pode considerar fazer algumas alterações de refatoração para melhorar a estrutura do código antes de estendê-la. Consulte [aprimorando a estrutura do código](#Improving).

|**To**|**Execute estas etapas**|
|-|-|
|Excluir uma dependência que não deveria existir|Clique na dependência e pressione **delete**.|
|Alterar ou restringir a direção de uma dependência|Defina sua propriedade **Direction** .|
|Criar novas dependências|Use as **ferramentas dependência e** **dependência bidirecional** .<br /><br /> Para desenhar várias dependências, clique duas vezes na ferramenta. Quando tiver terminado, clique na ferramenta **ponteiro** ou pressione a tecla **ESC** .|
|Especificar que os artefatos associados a uma camada não dependem dos namespaces especificados|Digite os namespaces na propriedade **dependências de namespace proibido** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|
|Especificar que os artefatos associados a uma camada não devem pertencer aos namespaces especificados|Digite os namespaces na propriedade de **namespaces proibidos** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|
|Especificar que os artefatos associados a uma camada devem pertencer a um dos namespaces especificados|Digite o namespace na propriedade **namespaces obrigatórios** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|

### <a name="Improving"></a>Melhorando a estrutura do código

As alterações de refatoração são melhorias que não afetam o comportamento do aplicativo, mas ajudam a facilitar a alteração e a extensão do código no futuro. O código bem estruturado tem um design que é fácil de abstrair para um diagrama de dependência.

Por exemplo, se você criar uma camada para cada namespace no código e, em seguida, fazer engenharia reversa das dependências, deverá haver um conjunto mínimo de dependências unidirecionais entre as camadas. Se você criar um diagrama mais detalhado usando classes ou métodos como suas camadas, o resultado também deverá ter as mesmas características.

Se esse não for o caso, o código será mais difícil de ser alterado durante sua vida e será menos adequado para validação usando diagramas de dependência.

## <a name="NewAreas"></a>Projetar novas áreas do seu aplicativo

Ao iniciar o desenvolvimento de um novo projeto ou uma nova área em um novo projeto, você pode desenhar camadas e dependências para ajudar a identificar os principais componentes antes de começar a desenvolver o código.

- **Mostrar padrões arquitetônicos identificáveis** em seus diagramas de dependência, se possível. Por exemplo, um diagrama de dependência que descreve um aplicativo de área de trabalho pode incluir camadas como apresentação, lógica de domínio e armazenamento de dados. Um diagrama de dependência que abrange um único recurso dentro de um aplicativo pode ter camadas como modelo, exibição e controlador. Para obter mais informações sobre esses padrões, consulte [padrões & práticas: arquitetura do aplicativo](http://go.microsoft.com/fwlink/?LinkId=145794).

- **Crie um artefato de código para cada camada** , como um namespace, uma classe ou um componente. Isso torna mais fácil seguir o código e vincular os artefatos de código a camadas. Assim que você criar cada artefato, vincule-o à camada apropriada.

- **Você não precisa vincular a maioria das classes e outros artefatos a camadas** porque eles se enquadram em artefatos maiores, como namespaces que você já vinculou a camadas.

- **Crie um novo diagrama para um novo recurso**. Normalmente, haverá um ou mais diagramas de dependência que descrevem todo o aplicativo. Se você estiver criando um novo recurso dentro do aplicativo, não adicione nem altere os diagramas existentes. Em vez disso, crie seu próprio diagrama que reflita as novas partes do código. As camadas no novo diagrama podem incluir camadas de apresentação, lógica de domínio e banco de dados para o novo recurso.

     Quando você cria o aplicativo, seu código será validado em relação ao diagrama geral e ao diagrama de recursos mais detalhado.

## <a name="EditLayout"></a>Editar o layout para apresentação e discussão

Para ajudá-lo a identificar camadas e dependências ou discuti-las com membros da equipe, edite a aparência e o layout do diagrama das seguintes maneiras:

- Altere os tamanhos, as formas e as posições das camadas.

- Altere as cores das camadas e dependências.

  - Selecione uma ou mais camadas ou dependências, clique com o botão direito do mouse e clique em **Propriedades**. Na janela **Propriedades** , edite a propriedade **Color** .

## <a name="Validate"></a>Validar o código em relação ao diagrama

Quando tiver editado o diagrama, você poderá validá-lo no código manualmente a qualquer momento ou automaticamente toda vez que criar.

Consulte:

- [Validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md)

- [Incluir validação de camada no processo de compilação](#BuildValidation)

## <a name="UpdateCode"></a>Atualizar o código para estar em conformidade com a nova arquitetura

Normalmente, os erros serão exibidos na primeira vez que você validar o código em relação a um diagrama de dependência atualizado. Esses erros podem ter várias causas:

- Um artefato é atribuído à camada errada. Nesse caso, mova o artefato.

- Um artefato como, por exemplo, uma classe usa outra classe de maneira a entrar em conflito com a arquitetura. Nesse caso, refatore o código para remover a dependência.

Para resolver esses erros, atualize o código até que mais nenhum erro seja exibido durante a validação. Isso geralmente é um processo iterativo. Para obter mais informações sobre esses erros, consulte [validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> À medida que desenvolver ou refatorar o código, você poderá ter novos artefatos para vincular ao diagrama de dependência. No entanto, isso pode não ser necessário, por exemplo, quando você tem camadas que representam namespaces existentes, e o novo código só adiciona mais material a esses namespaces.

Durante o processo de desenvolvimento, você talvez queira suprimir alguns dos conflitos reportados durante a validação. Por exemplo, você talvez queira suprimir erros que já esteja resolvendo ou que não sejam relevantes para seu cenário específico. Ao suprimir um erro, é uma prática recomendada registrar um item de trabalho no Team Foundation. Para executar essa tarefa, consulte [validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a>Incluir validação de camada no processo de compilação

Para garantir que as alterações futuras no código estejam em conformidade com os diagramas de dependência, inclua a validação de camada no processo de compilação padrão da solução. Sempre que outros membros da equipe criarem a solução, quaisquer diferenças entre as dependências no código e no diagrama de dependência serão relatadas como erros de compilação. Para obter mais informações sobre como incluir a validação de camada no processo de compilação, consulte [validar código com diagramas de dependência](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Consulte também

- [Diagramas de dependência: referência](../modeling/layer-diagrams-reference.md)
- [Criar diagramas de dependência usando seu código](../modeling/create-layer-diagrams-from-your-code.md)
