---
title: Criar diagramas de camada do seu código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e6cd77e785adb59fc8b2cf3b28724ed0efe1ae3
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300276"
---
# <a name="create-layer-diagrams-from-your-code"></a>Criar diagramas de camada por meio de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para visualizar a arquitetura lógica de alto nível do sistema de software, crie um *diagrama de camada* no Visual Studio. Para garantir que seu código permaneça consistente com esse design, valide seu código com um diagrama de camada. É possível criar diagramas de camada para projetos do Visual C# .NET e do Visual Basic .NET. Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

 ![Criar um diagrama de camadas](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")

 Um diagrama de camada permite organizar itens de solução do Visual Studio em grupos abstratos, lógicos, chamados de *camadas*. É possível usar camadas para descrever as tarefas principais realizadas por esses artefatos ou os componentes principais do sistema. Cada camada pode conter outras camadas que descrevem tarefas mais detalhadas. Também é possível especificar as *dependências* desejadas ou existentes entre camadas. Essas dependências, representadas como setas, mostram quais camadas podem usar ou atualmente usam a funcionalidade representada por outras camadas. Para manter controle arquitetônico do código, mostre as dependências desejadas no diagrama e, em seguida, valide o código no diagrama.

## <a name="CreateDiagram"></a>Criar um diagrama de camadas
 Antes de criar um diagrama de camada, verifique se a solução tem um projeto de modelagem. Confira [criar diagramas e projetos de modelagem UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

> [!IMPORTANT]
> Não adicione, arraste ou copie um diagrama de camada existente de um projeto de modelagem a outro projeto de modelagem ou a outro local na solução. Isso preserva as referências do diagrama original, mesmo que você altere o diagrama. Isso também impede que a validação da camada funcione corretamente e talvez cause outros problemas como, por exemplo, elementos não encontrados ou outros erros quando você tenta abrir o diagrama.
>
> Em vez disso, adicione um novo diagrama de camada ao projeto de modelagem. Copie os elementos do diagrama de origem para o novo diagrama. Salve o projeto de modelagem e o novo diagrama de camada.

#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Para adicionar um novo diagrama de camada a um projeto de modelagem

1. No menu **arquitetura** , escolha **novo UML ou diagrama de camada**.

2. Em **Modelos**, escolha **Diagrama de Camada**.

3. Nomeie o diagrama.

4. Em **Adicionar ao Projeto de Modelagem**, navegue até e selecione um projeto de modelagem existente na solução.

     - ou -

     Escolha **Criar um novo projeto de modelagem** para adicionar um novo projeto de modelagem à solução.

    > [!NOTE]
    > O diagrama de camada deve estar dentro de um projeto de modelagem. Porém, é possível vinculá-lo a itens em qualquer lugar na solução.

5. Não se esqueça de salvar o projeto de modelagem e o diagrama de camada.

## <a name="CreateLayers"></a>Criar camadas de artefatos
 É possível criar camadas dos itens de solução do Visual Studio como, por exemplo, projetos, arquivos de código, namespaces, classes e métodos. Isso cria automaticamente links entre camadas e itens, incluindo-os no processo de validação da camada.

 Também é possível vincular camadas a itens que não dão suporte à validação como, por exemplo, documentos do Word ou apresentações do Powerpoint, de forma que você pode associar uma camada a especificações ou planos. Também é possível vincular camadas a arquivos em projetos compartilhados entre vários aplicativos, mas o processo de validação não incluirá essas camadas, exibidas com nomes genéricos como, por exemplo, "Camada 1" e "Camada 2".

 Para saber se um item vinculado dá suporte à validação, abra **Gerenciador de Camadas** e examine a propriedade **Dá Suporte à Validação** do item. Consulte [Gerenciando links para artefatos](#Managing).

|**To**|**Siga estas etapas**|
|------------|----------------------------|
|Criar uma camada para um único artefato|<ol><li>Arraste o item para o diagrama de camada destas fontes:<br /><br /> <ul><li>**Gerenciador de Soluções**<br /><br />         Por exemplo, é possível arrastar arquivos ou projetos.</li><li>Mapas de código<br /><br />         Consulte [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md) e [usar mapas de código para depurar seus aplicativos](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Pesquisador** de **modo de exibição de classe** ou objeto</li></ul><br />     Uma camada é exibida no diagrama e está vinculada ao artefato.</li><li>Renomeie a camada para refletir as responsabilidades do código ou dos artefatos associados.</li></ol> **Importante:**  Arrastar arquivos binários para o diagrama de camada não adiciona automaticamente suas referências ao projeto de modelagem. Você deve adicionar manualmente os arquivos binários que você deseja validar ao projeto de modelagem. **Para adicionar arquivos binários ao projeto de modelagem** <ol><li>No **Gerenciador de Soluções**, abra o menu de atalho do projeto de modelagem e, em seguida, escolha **Adicionar Item Existente**.</li><li>Na caixa de diálogo **Adicionar Item Existente**, navegue até os arquivos binários, selecione-os e, em seguida, escolha **OK**.     Os arquivos binários são exibidos no projeto de modelagem.</li><li>No **Gerenciador de Soluções**, escolha um arquivo binário adicionado e, em seguida, pressione **F4** para abrir a janela **Propriedades**.</li><li>Em cada arquivo binário, defina a propriedade **Compilar Ação** como **Validar**.</li></ol>|
|Criar uma única camada para todos os artefatos selecionados|Arraste todos os artefatos para o diagrama de camada ao mesmo tempo.<br /><br /> Uma camada é exibida no diagrama e está vinculada a todos os artefatos.|
|Criar uma camada para cada artefato selecionado|Mantenha a tecla **SHIFT** pressionada enquanto arrasta todos os artefatos para o diagrama de camada ao mesmo tempo. **Observação:**  Se você usar a tecla **Shift** para selecionar um intervalo de itens, libere a chave depois de selecionar os artefatos. Mantenha-o pressionado novamente ao arrastar os artefatos para o diagrama. <br /><br /> Uma camada para cada artefato é exibida no diagrama e está vinculada a cada artefato.|
|Adicionar um artefato a uma camada|Arraste o artefato à camada.|
|Criar uma nova camada desvinculada|Na **Caixa de Ferramentas**, expanda a seção **Diagrama de Camada** e, em seguida, arraste uma **Camada** para o diagrama de camada.<br /><br /> Para adicionar várias camadas, clique duas vezes na ferramenta. Quando você terminar, escolha a ferramenta **Ponteiro** ou pressione a tecla **ESC**.<br /><br /> - ou -<br /><br /> Abra o menu de atalho do diagrama de camada e, em seguida, escolha **Adicionar** e **Camada**.|
|Criar camadas aninhadas|Arraste uma camada existente para outra camada.<br /><br /> - ou -<br /><br /> Abra o menu de atalho de uma camada e, em seguida, escolha **Adicionar** e **Camada**.|
|Criar uma nova camada que contém duas ou mais camadas existentes|Selecione as camadas, abra o menu de atalho da seleção e, em seguida, escolha **Grupo**.|
|Alterar a cor de uma camada|Defina a propriedade **Cor** como a cor desejada.|
|Especificar que os artefatos associados a uma camada não devem pertencer aos namespaces especificados|Digite os namespaces na propriedade **Namespaces Proibidos** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|
|Especificar que os artefatos associados a uma camada não dependem dos namespaces especificados|Digite os namespaces na propriedade **Dependências de Namespace Proibidas** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|
|Especificar que os artefatos associados a uma camada devem pertencer a um dos namespaces especificados|Digite o namespace na propriedade **Namespaces Obrigatórios** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|

 O número em uma camada indica o número de artefatos que estão associados à camada. No entanto, ao ler esse número, lembre-se do seguinte:

- Se uma camada estiver vinculada a um artefato que contenha outros artefatos, mas não estiver vinculada diretamente a outros artefatos, o número incluirá apenas o artefato vinculado. No entanto, os outros artefatos estão incluídos para análise durante a validação da camada.

     Por exemplo, se uma camada estiver vinculada a um único namespace, o número de artefatos vinculados será 1, mesmo se o namespace contiver classes. Se a camada também tiver links para cada classe no namespace, o número incluirá as classes vinculadas.

- Se uma camada contiver outras camadas vinculadas a artefatos, a camada de contêiner também estará vinculada a esses artefatos, mesmo que o número na camada de contêiner não inclua esses artefatos.

## <a name="Managing"></a>Gerenciar links entre camadas e artefatos

1. No diagrama de camada, abra o menu de atalho da camada e, em seguida, escolha **Exibir Links**.

     O **Gerenciador de camadas** mostra os links de artefatos para a camada selecionada.

2. Use as seguintes tarefas para gerenciar esses links:

|**To**|**No Gerenciador de camadas**|
|------------|---------------------------|
|Excluir o links entre a camada e um artefato|Abra o menu de atalho do link de artefato e, em seguida, escolha **Excluir**.|
|Mover o link de uma camada para outra|Arraste o link de artefato para uma camada existente no diagrama.<br /><br /> - ou -<br /><br /> 1. Abra o menu de atalho para o link do artefato e, em seguida, escolha **recortar**.<br />2. no diagrama de camada, abra o menu de atalho da camada e escolha **colar**.|
|Copiar o link de uma camada para outra|1. Abra o menu de atalho para o link do artefato e, em seguida, escolha **copiar**.<br />2. no diagrama de camada, abra o menu de atalho da camada e escolha **colar**.|
|Criar uma nova camada com base em um link de artefato existente|Arraste o link de artefato para uma área em branco no diagrama.|
|Verifique se um artefato vinculado dá suporte à validação no diagrama de camada.|Observe a coluna **Dá Suporte à Validação** do link de artefato.|

## <a name="Discovering"></a>Dependências existentes de engenharia reversa
 Existirá uma dependência sempre que um artefato associado a uma camada tiver uma referência a um artefato associado a outra camada. Por exemplo, uma classe em uma camada declara uma variável que tem uma classe em outra camada. É possível fazer engenharia reversa em dependências existentes para artefatos vinculados a camadas no diagrama.

> [!NOTE]
> As dependências não podem sofrer engenharia reversa para determinados tipos de artefatos. Por exemplo, nenhuma dependência sofrerá engenharia reversa de ou para uma camada vinculada a um arquivo de texto. Para saber quais artefatos têm dependências que é possível sofrer engenharia reversa, abra o menu de atalho de uma ou mais camadas e, em seguida, escolha **Exibir Links**. Em **Gerenciador de Camadas**, examine a coluna **Dá Suporte à Validação**. As dependências não sofrerão engenharia reversa para artefatos para os quais essa coluna mostra **Falso**.

- Selecione uma ou mais camadas, abra o menu de atalho de uma camada selecionada e, em seguida, escolha **Gerar Dependências**.

  Normalmente, você verá algumas dependências que não devem existir. É possível editar essas dependências para alinhá-las com o design desejado.

## <a name="EditDependencies"></a>Editar camadas e dependências para mostrar o design pretendido
 Para descrever as alterações que você pretende fazer no sistema ou na arquitetura desejada, edite o diagrama de camada:

|**To**|**Execute estas etapas**|
|------------|-----------------------------|
|Alterar ou restringir a direção de uma dependência|Defina sua propriedade **Direção**.|
|Criar novas dependências|Use as ferramentas **Dependência** e **Dependência Bidirecional**.<br /><br /> Para desenhar várias dependências, clique duas vezes na ferramenta. Quando você terminar, escolha a ferramenta **Ponteiro** ou pressione a tecla **ESC**.|
|Especificar que os artefatos associados a uma camada não dependem dos namespaces especificados|Digite os namespaces na propriedade **Dependências de Namespace Proibidas** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|
|Especificar que os artefatos associados a uma camada não devem pertencer aos namespaces especificados|Digite os namespaces na propriedade **Namespaces Proibidos** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|
|Especificar que os artefatos associados a uma camada devem pertencer a um dos namespaces especificados|Digite o namespace na propriedade **Namespaces Obrigatórios** da camada. Use um ponto-e-vírgula ( **;** ) para separar os namespaces.|

## <a name="EditLayout"></a>Alterar como os elementos aparecem no diagrama
 É possível alterar o tamanho, a forma, a cor e a posição das camadas ou a cor das dependências editando-se suas propriedades.

## <a name="Codemaps"></a>Descobrir padrões e dependências em um mapa de código
 Ao criar diagramas de camada, você também pode criar **mapas de código**. Esses diagramas podem ajudá-lo a descobrir padrões e dependências enquanto explora o código. Use Gerenciador de Soluções, Modo de Exibição de Classe ou pesquisador de objetos para explorar assemblies, namespaces e classes, que geralmente correspondem bem às camadas existentes. Para obter mais informações sobre mapas de código, consulte:

- [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)

- [Usar mapas de códigos para depurar aplicativos](../modeling/use-code-maps-to-debug-your-applications.md)

- [Encontrar possíveis problemas usando analisadores de mapa de códigos](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Consulte também
 [Vídeo do Channel 9: design e validação de sua arquitetura usando](https://go.microsoft.com/fwlink/?LinkID=252073) diagramas de camada Diagrams de camada [:](../modeling/layer-diagrams-reference.md) [diagramas de camada de referência: diretrizes](../modeling/layer-diagrams-guidelines.md) [validam código com diagramas de camada](../modeling/validate-code-with-layer-diagrams.md) [Visualizar código](../modeling/visualize-code.md)