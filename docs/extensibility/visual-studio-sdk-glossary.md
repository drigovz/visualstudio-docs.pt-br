---
title: Visual Studio SDK Glossário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 332e606e689e9394f2fcdc8cbc902e2d4a6e5ab5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698163"
---
# <a name="visual-studio-sdk-glossary"></a>Glossário Visual Studio SDK
Este glossário fornece definições para termos [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] que são usados na documentação.

## <a name="terms"></a>Termos
 add-in Um aplicativo utilitário, driver ou outro software adicionado a um aplicativo principal. No ambiente de desenvolvimento integrado (IDE) do Visual Studio, um complemento é um aplicativo baseado em automação que amplia os recursos do IDE.

 modelo de automação O modelo de automação, conhecido nas versões anteriores do Visual Studio como modelo de extensibilidade, é uma interface de programação que lhe dá acesso às rotinas subjacentes que impulsionam o IDE. Os complementos, assistentes e macros usam objetos no modelo de automação para controlar ou estender a funcionalidade do IDE.

 comando UI context Association of a GUID com a visibilidade de um comando ou elemento de interface do usuário, como uma barra de ferramentas. O contexto de Interface do Comando é diferente do contexto de seleção, pois não está conectado a uma janela.

 O contexto da Interface do Comando pode ser usado para:

- Atribua um GUID a uma barra de ferramentas que aparece quando uma janela em particular é ativada.

- Atribua um GUID à disponibilidade de um comando sem ter que carregar ou executar um VSPackage.

- Atribuir um GUID para afetar a vinculação da tecla ativa.

- Atribua um GUID para ativar a gravação de macro.

- Atribua um GUID para ativar o modo de depuração ou alternar entre o design e o modo de execução em um editor.

  componente Peça de software que pode ser feito parte da funcionalidade de um aplicativo sem que esse aplicativo tenha qualquer informação pré-existente sobre a implementação do software. A comunicação entre um componente e um aplicativo é exclusivamente através de interfaces de estilo OLE.

  gerenciador de `SOleComponentManager`componentes Um serviço, que fornece serviços de coordenação de interface não-usuário para componentes de nível superior. O `SOleComponentManager` serviço implementa a `IOleComponentManager` interface.

  gerenciador de interface `SOleComponentUIManager`do usuário Um serviço, que fornece serviços de coordenação de interface de usuário. O `SOleComponentUIManager` serviço implementa as `IOleComponentUIManager` interfaces e `IOleInPlaceComponentUIManager` interfaces.

  saco de `IVsUserContext` contexto Um objeto (objeto COM) anexado a um componente do ambiente. Este objeto contém palavras-chave de pesquisa, palavras-chave **F1** e atributos que se relacionam com o componente. Sacos de contexto também apontam para quaisquer sacos de subcontexto que estejam ligados a eles.

  provedor de contexto Um componente no IDE que tem um saco de contexto associado a ele. Esses componentes incluem uma janela de ferramenta, editor ou hierarquia de projeto.

  designer Uma interface de programação que permite aos usuários manipular elementos da interface do usuário (formulários, botões e outros controles).

  DocData Um objeto COM encapsulando os dados subjacentes de um documento em um mundo onde há separação de documentos/visualizações (por exemplo, no caso do editor de texto, este seria o buffer de texto subjacente a todas as visualizações do editor de texto). Se a Fábrica de Editores não fornecer este objeto, o IDE fabrica um em seu nome. A responsabilidade deste objeto é gerenciar a persistência de dados e o `DocData`compartilhamento de semântica para múltiplas visualizações sobre este mesmo . Se `DocData` o objeto `IOleCommandTarget` suportar a interface, ele será incluído no roteamento de comando do UIShell.

  Tecnologia DocObject usada para hospedar a ui dentro de um quadro fornecido pelo host. Mais especificamente, este termo refere-se a qualquer `IOleDocument` incorporação que suporte as interfaces relacionadas. Essa tecnologia tem muitas aplicações potenciais, como um detalhe de implementação de documentos COM, janelas de ferramentas no Visual Basic 5.0, designers ActiveX no Visual Basic 6.0, e assim por diante.

  documento Usado para se referir genericamente ao `DocData` documento `DocView`como um todo — tanto o e o . Por exemplo, um DocumentFrame contém um `DocView`, mas `DocData` também retém uma referência à persistência para lidar com o manuseio.

  DocView The DocObject/Inbedding/WindowPane com o qual o usuário `DocData`interage para visualizar e manipular o subjacente . Os usuários não aproveitam a separação Document/View `DocObject` que faz parte do design da interface. Os usuários usam um DocObject inteiro para agir como uma visão em vez de usar `DocData`uma noção mais abstrata (e menos formalizada) de dados subjacentes conhecidos como . `DocView`objetos são sempre incorporados com objetos de quadro de documento (janelas de criança MDI) do IDE.

  DTE `DTE` O objeto (Extensibility ferramentas de desenvolvimento) é o ponto de acesso mais alto no modelo de automação do Visual Studio, que permite automatizar e estender o IDE de forma programática.

  Janela de ajuda dinâmica Janela de ferramentas que é implementada pelo IDE e exibe uma lista de tópicos de palavra-chave de procurar ou **F1.**

  código de editor (classe, CLSID) que implementa o `DocView`. Ele também `DocData` implementa se a exibição e a separação de dados forem suportadas.

  extensão Um recurso que modifica, personaliza ou adiciona a um IDE. Você cria extensões usando o modelo de automação ou VSPackages.

  editor externo Um editor que não é específico do IDE, como o Microsoft Word. Ele foi registrado através de mecanismos próprios e pode ser usado fora do IDE. Se este editor pode ser incorporado, ele aparecerá dentro de uma janela no IDE. Se não puder ser incorporado, uma janela de nível superior separada será criada.

  hierarquia Árvore de nódulos, cada nó associado a um conjunto de propriedades.

  componente de nível superior independente Um componente que usa uma janela de nível superior modeless e pode operar efetivamente como uma janela de aplicativo independente, mas é implementado como um objeto em processo. Portanto, um componente independente de nível superior deve coordenar a modalidade e os serviços de loop de mensagem com o IDE. Objetos em processo não têm seu próprio loop de mensagem.

  provedor de informações O provedor de informações é um módulo que pode procurar `IVsUserContextItem` palavras-chave e retornar uma lista de tópicos, na forma de objetos. Para fornecer itens de palavra-chave **de F1** e busca para o provedor de informações, registre seu arquivo de ajuda compilado (*. HxS*) com o sistema. Os tópicos de Ajuda nesses arquivos fornecem a lista de tópicos exibidos na janela Ajuda Dinâmica e mostram se um usuário pressiona **F1**.

  componente no lugar Um objeto VSPackage `IOleInPlaceComponent` que implementa a interface para gerenciar uma janela que está visualmente contida dentro de uma janela de documento de propriedade do IDE. Os componentes no local não participam da fusão padrão do menu OLE; em vez disso, eles integram seus elementos de interface de usuário no IDE.

  Existem dois tipos de componentes no local: componentes no lugar e controles de componentes.

  Os componentes no lugar conectados têm menus, barras de ferramentas e comandos que são integrados firmemente na interface do usuário do IDE, aparecendo como se fossem incorporados diretamente ao IDE.

  Os controles de componentes não possuem nenhum dos seus próprios elementos de interface de usuário integrados ao IDE; em vez disso, eles usam menus, comandos e barras de ferramentas do IDE. Por exemplo, o comando Bold pode ser usado para ousar uma palavra selecionada dentro de um rico controle de texto incorporado em um formulário. No entanto, os controles de componentes podem solicitar que elementos de ia específicos de componentes instalados dinamicamente sejam exibidos.

  serviço de idioma Um conjunto de objetos que permite aos desenvolvedores do VSPackage implementar recursos de editores de código de linguagem de computador, como marcação de texto e coloração.

  Projeto de arquivos diversos usado para abrigar arquivos abertos que não estão em nenhum projeto. A lista de itens deste projeto não é persistiu.

  projetos Os projetos são compostos por objetos `IVsHierarchy` de hierarquia ou objetos COM que implementam a interface.

  designer ou editor específico de projeto Um designer que não pode ser usado independentemente do tipo de projeto. Todos os designers específicos do projeto devem inserir suas informações da Fábrica do Editor no registro. O IDE, então, pode instanciar o designer sempre que um determinado tipo de arquivo é aberto em um projeto específico.

  janela tipo projeto Uma janela que rastreia constantemente a hierarquia e o item do projeto atualmente ativos do contexto de seleção global. As janelas do `SVsTrackSelectionEx` tipo projeto usam o serviço para alertar o IDE de alterações e exibir feedback para o usuário. O Solution Explorer é um exemplo de uma janela do tipo projeto.

  Janela de propriedades Anteriormente, navegador de propriedades.

  projetos baseados em referência Projeto que não requer que os arquivos para o projeto estejam no mesmo diretório. Em vez disso, as referências a arquivos de outros diretórios não relacionados são armazenadas e mantidas pelo próprio projeto.

  executando tabela de documentos Estrutura interna pela qual o IDE mantém a lista de todos os documentos atualmente abertos. A lista inclui todos os documentos abertos na memória, independentemente de os documentos estarem sendo editados. Um documento é qualquer item que é salvo, incluindo procedimentos armazenados abertos em um editor, arquivos em um projeto ou o arquivo principal do projeto (por exemplo, *.vcproj file).

  contexto de seleção Dados que fazem parte do detalhe de cada janela no IDE e são usados para rastrear seleções ativas. O contexto de seleção consiste em:

- Ponteiro para `IVsHierarchy` a interface da hierarquia do projeto

- Identificador de item do item do projeto.

- Ponteiro para `ISelectionContainer` a interface que fornece acesso às propriedades dos objetos ativos.

- Matriz de valores de elementos.

  serviço Um contrato para um conjunto de interfaces COM que reside em um único objeto COM. Quando você cria um serviço, que é identificado por um GUID, você define o conjunto de interfaces COM que executa o serviço. Os objetos COM usam serviços para se comunicarem entre si.

  grupo de soluções de projetos relacionados com os quais um usuário trabalha.

  designer padrão Um designer que pode ser usado independente do tipo de projeto. Todos os designers padrão devem inserir suas informações da Fábrica do Editor no registro. O IDE, então, pode instanciar o designer sempre que um arquivo com uma extensão específica for aberto. Os dados devem persistir em um arquivo.

  editor padrão Editor que pode ser usado independente de qualquer tipo de projeto em particular. Esses editores têm editores registrados no registro. Isso permite que o IDE localize e invoque o editor.

  editor padrão do SISTEMA OPERACIONAL Uma incorporação que não é específica do Visual Studio. Ele é registrado usando as conhecidas teclas Win32 (por exemplo, o Win32 Explorer sabe como invocar). Se tal editor pode ser incorporado, o editor ainda aparece em seu lugar no IDE. Caso contrário, uma janela de nível superior separada é criada para esses editores.

  saco de `IVsUserContext` subcontexto Um objeto ligado a um saco de contexto. O objeto contém palavras-chave de pesquisa, palavras-chave **F1** e atributos para uma seleção dentro de um componente IDE. Exemplos de subcontexto incluem um comando em uma janela de ferramenta ou uma palavra-chave em um editor.

  Lista de tarefas Janela de ferramentas que é implementada pelo IDE e exibe uma lista de tarefas ativas.

  buffer de texto Nome `VSTextBuffer`comum para o objeto .

  Exibição de texto `VSTextView`Nome comum para o objeto .

  componente de nível superior da ferramenta Um componente que funciona como uma janela popup modeless, coordenando firmemente com a interface de usuário do IDE. Como componentes independentes de nível superior, os componentes de nível superior da ferramenta também devem coordenar os serviços de modalidade e loop de mensagem com o IDE.

  componente de nível superior Um objeto VSPackage que gerencia uma janela de nível superior modeless em vez da área cliente de uma janela IDE. Componentes de alto `IOleComponent` nível implementam a interface para aproveitar os serviços de loop de mensagem, como acesso ao tempo ocioso.

  UI ativo Um objeto VSPackage que é visível e atualmente tem foco.

  Hierarquia de interface Um objeto COM `IVsUIHierarchy` que implementa a interface para permitir a exibição de uma hierarquia. A janela de hierarquia de `ISelectionContainer` interface de interface implementa a interface para atualizar a janela Propriedades; outras janelas do tipo projeto podem usar essa implementação, se desejar.

  Tabela de comando do VSCT Visual Studio. O arquivo .vsct contém informações sobre a colocação e comportamentos de menus, barras de ferramentas e comandos no formato XML.

  VSPackage Um software instalável que estende o Visual Studio IDE contribuindo com um ou mais dos seguintes itens: interface de usuário, serviços, tipos de projeto ou editor/designer. Um VSPackage consiste em um objeto `IVsPackage` COM que implementa a interface e um ou mais outros objetos COM que implementam outras interfaces para suportar a seleção e outros recursos. Além disso, um VSPackage tem requisitos específicos de registro.
