---
title: Glossário do SDK do Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c189c4c9e06d224d7cef296a2c39e732cbc29f6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538701"
---
# <a name="visual-studio-sdk-glossary"></a>Glossário do SDK do Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este glossário fornece definições para termos que são usados na [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] documentação do.  
  
## <a name="terms"></a>Termos  
 add-in  
 Um aplicativo de utilitário, driver ou outro software adicionado a um aplicativo primário. No IDE (ambiente de desenvolvimento integrado) do Visual Studio, um suplemento é um aplicativo baseado em automação que estende os recursos do IDE.  
  
 modelo de automação  
 O modelo de automação, conhecido em versões anteriores do Visual Studio como o modelo de extensibilidade, é uma interface de programação que fornece acesso às rotinas subjacentes que orientam o IDE. Os suplementos, assistentes e macros usam objetos no modelo de automação para controlar ou estender a funcionalidade do IDE.  
  
 contexto da interface do usuário do comando  
 Associação de um GUID com a visibilidade de um comando ou elemento de interface do usuário, como uma barra de ferramentas. O contexto da interface do usuário do comando é diferente do contexto de seleção, pois não está anexado a uma janela.  
  
 O contexto da interface do usuário do comando pode ser usado para:  
  
- Atribua um GUID a uma barra de ferramentas que aparece quando uma janela específica é ativada.  
  
- Atribua um GUID à disponibilidade de um comando sem precisar carregar ou executar um VSPackage.  
  
- Atribua um GUID para afetar a associação de chave ativa.  
  
- Atribua um GUID para ativar a gravação de macro.  
  
- Atribua um GUID para ativar o modo de depuração ou para alternar entre o modo de design e de execução em um editor.  
  
  componente  
  Parte do software que pode se tornar parte da funcionalidade de um aplicativo sem que o aplicativo tenha informações preexistentes sobre a implementação do software. A comunicação entre um componente e um aplicativo é exclusivamente por meio de interfaces de estilo OLE.  
  
  Gerenciador de componentes  
  Um serviço, `SOleComponentManager` , que fornece serviços de coordenação de interface que não são do usuário para componentes de nível superior. O `SOleComponentManager` serviço implementa a `IOleComponentManager` interface.  
  
  Gerenciador de interface do usuário do componente  
  Um serviço, `SOleComponentUIManager` , que fornece serviços de coordenação de interface do usuário. O `SOleComponentUIManager` serviço implementa as `IOleComponentUIManager` `IOleInPlaceComponentUIManager` interfaces e.  
  
  recipiente de contexto  
  Um `IVsUserContext` objeto (objeto com) anexado a um componente de ambiente. Esse objeto contém palavras-chave de pesquisa, palavras-chave F1 e atributos relacionados ao componente. Além disso, os pacotes de contexto apontam para os pacotes de subcontexto que estão vinculados a eles.  
  
  provedor de contexto  
  Um componente no IDE que tem um recipiente de contexto associado a ele. Esses componentes incluem uma janela de ferramentas, um editor ou uma hierarquia de projeto.  
  
  designer  
  Uma interface de programação que permite aos usuários manipular elementos da interface do usuário (formulários, botões e outros controles).  
  
  DocData  
  Um objeto COM encapsulando os dados subjacentes de um documento em um mundo em que há separação de documento/exibição (por exemplo, no caso do editor de texto, esse seria o buffer de texto subjacente a todas as exibições do editor de texto). Se o EditorFactory não fornecer esse objeto, o IDE fabricará um em seu nome. A responsabilidade desse objeto é gerenciar a persistência de dados e a semântica de compartilhamento para várias exibições acima dessa mesma `DocData` . Se o `DocData` objeto der suporte à `IOleCommandTarget` interface, ele será incluído no roteamento de comandos do UIShell.  
  
  DocObject  
  Tecnologia usada para hospedar a interface do usuário em um quadro fornecido pelo host. Mais especificamente, esse termo refere-se a qualquer inserção que dê suporte às `IOleDocument` interfaces relacionadas ao e ao. Essa tecnologia tem muitos aplicativos potenciais, como um detalhe de implementação de documentos COM, janelas de ferramentas no Visual Basic 5,0, designers do ActiveX em Visual Basic 6,0 e assim por diante.  
  
  documento  
  Usado para fazer referência genérica ao documento como um todo – o `DocData` e o `DocView` . Por exemplo, um DocumentFrame contém um `DocView` , mas também retém uma referência ao `DocData` para lidar com a persistência.  
  
  DocView  
  O DocObject/incorporação/WindowPane com o qual o usuário interage para exibir e manipular o subjacente `DocData` . Observe que os usuários não tiram proveito da separação de documento/exibição que faz parte do `DocObject` design da interface. Os usuários usam um DocObject inteiro para agir como uma exibição em vez de usar uma noção mais abstrata (e menos formalizada) dos dados subjacentes conhecidos como `DocData` . `DocView` os objetos sempre são inseridos com objetos de quadro de documento (janelas filho MDI) do IDE.  
  
  ESTABELECIDA  
  O `DTE` objeto (extensibilidade de ferramentas de desenvolvimento) é o ponto de acesso mais alto no modelo de automação do Visual Studio, que permite automatizar e estender programaticamente o IDE.  
  
  Janela de ajuda dinâmica  
  Janela de ferramentas implementada pelo IDE e exibe uma lista de tópicos de ajuda de palavras-chave de pesquisa ou F1.  
  
  editor  
  Código (classe, CLSID) que implementa o `DocView` . Ele também implementa `DocData` se a exibição/separação de dados tem suporte.  
  
  extensão  
  Um recurso que modifica, personaliza ou adiciona a um IDE. Você cria extensões usando o modelo de automação ou VSPackages.  
  
  editor externo  
  Um editor que não é específico do IDE, como o Microsoft Word. Ele foi registrado por meio de seus próprios mecanismos e pode ser usado fora do IDE. Se esse editor puder ser inserido, ele aparecerá dentro de uma janela no IDE. Se não puder ser inserido, uma janela de nível superior separada será criada.  
  
  hierarquia  
  Árvore de nós, cada nó associado a um conjunto de propriedades.  
  
  componente de nível superior independente  
  Um componente que usa uma janela de nível superior não sem-modo e pode operar efetivamente como uma janela de aplicativo autônoma, mas é implementado como um objeto em processo. Portanto, um componente de nível superior independente deve coordenar a modalidade e os serviços de loop de mensagem com o IDE. Os objetos em processo não têm seu próprio loop de mensagem.  
  
  provedor de informações  
  O provedor de informações é um módulo que pode pesquisar palavras-chave e retornar uma lista de tópicos, na forma de `IVsUserContextItem` objetos. Para fornecer F1 e pesquisar itens de palavra-chave para o provedor de informações, registre o arquivo de ajuda compilado (. HxS) com o sistema. Os tópicos de ajuda nesses arquivos são usados para fornecer a lista de tópicos exibidos na janela de ajuda dinâmica e mostram se um usuário pressiona F1.  
  
  componente in-loco  
  Um objeto VSPackage que implementa a `IOleInPlaceComponent` interface para gerenciar uma janela que está visualmente contida em uma janela de documento pertencente ao IDE. Os componentes in-loco não participam da mesclagem de menus OLE padrão; em vez disso, eles integram seus elementos de interface do usuário no IDE.  
  
  Há dois tipos de componentes in-loco: componentes in-loco vinculados e controles de componente.  
  
  Os componentes in-loco vinculados têm menus, barras de ferramentas e comandos que são integrados rigidamente à interface do usuário do IDE, aparecendo como se estivessem criados diretamente no IDE.  
  
  Controles de componente não têm nenhum dos seus próprios elementos de interface do usuário integrados ao IDE; em vez disso, eles usam os menus, comandos e barras de ferramentas do IDE. Por exemplo, o comando Bold poderia ser usado para negrito de uma palavra selecionada dentro de um controle Rich Text inserido em um formulário. No entanto, os controles de componente podem solicitar que os elementos de interface do usuário específicos do componente instalados dinamicamente sejam exibidos.  
  
  serviço de linguagem  
  Um conjunto de objetos que permite aos desenvolvedores de VSPackage implementar recursos de editores de código de idioma do computador, como a marcação de texto e a coloração.  
  
  Projeto de arquivos diversos  
  Projeto usado para alojar arquivos abertos que não estão em nenhum projeto. A lista de itens neste projeto não é persistente.  
  
  project  
  Os projetos são compostos de objetos de hierarquia ou objetos COM que implementam a `IVsHierarchy` interface.  
  
  Designer ou editor específico do projeto  
  Um designer que não pode ser usado independentemente do tipo de projeto. Todos os designers específicos do projeto devem inserir suas informações de fábrica do editor no registro. Em seguida, o IDE pode instanciar o designer sempre que um determinado tipo de arquivo for aberto em um projeto específico.  
  
  janela de tipo de projeto  
  Uma janela que acompanha constantemente a hierarquia de projeto atualmente ativa e o item do contexto de seleção global. Janelas de tipo de projeto usam o `SVsTrackSelectionEx` serviço para alertar o IDE de alterações e exibir comentários para o usuário. Gerenciador de Soluções é um exemplo de uma janela de tipo de projeto.  
  
  Janela de Propriedades  
  Anteriormente navegador de propriedades.  
  
  projetos baseados em referência  
  Projeto que não exige que os arquivos do projeto estejam no mesmo diretório. Em vez disso, as referências a arquivos de outros diretórios não relacionados são armazenadas e mantidas pelo próprio projeto.  
  
  executando tabela de documentos  
  Estrutura interna pela qual o IDE mantém a lista de todos os documentos abertos no momento. Essa lista inclui todos os documentos abertos na memória, independentemente de os documentos estarem sendo editados no momento. Um documento é qualquer item salvo, incluindo procedimentos armazenados abertos em um editor, arquivos em um projeto ou no arquivo de projeto principal (por exemplo, arquivo *. vcproj).  
  
  contexto de seleção  
  Dados que fazem parte do detalhe de cada janela no IDE e são usados para controlar seleções ativas. O contexto de seleção consiste em:  
  
- Ponteiro para a `IVsHierarchy` interface da hierarquia do projeto  
  
- Identificador de item do item de projeto.  
  
- Ponteiro para a `ISelectionContainer` interface que fornece acesso a propriedades para os objetos ativos.  
  
- Matriz de valores de elemento.  
  
  serviço  
  Um contrato para um conjunto de interfaces COM que residem em um único objeto COM. Ao criar um serviço, que é identificado por um GUID, você define o conjunto de interfaces COM que executa o serviço. Objetos COM usam serviços para se comunicar uns com os outros.  
  
  solução  
  Grupo de projetos relacionados com os quais um usuário trabalha.  
  
  designer padrão  
  Um designer que pode ser usado independentemente do tipo de projeto. Todos os designers padrão devem inserir as informações de fábrica do editor no registro. Em seguida, o IDE pode instanciar o designer sempre que um arquivo com uma extensão específica for aberto. Os dados devem persistir em um arquivo.  
  
  editor padrão  
  Editor que pode ser usado independentemente de qualquer tipo de projeto específico. Esses editores têm EditorFactories registrados no registro. Isso permite que o IDE Localize e invoque o editor.  
  
  Editor de sistema operacional padrão  
  Uma incorporação que não é específica do Visual Studio. Ele é registrado usando as chaves Win32 conhecidas (por exemplo, o Win32 Explorer sabe como invocar). Se tal editor puder ser inserido, o editor ainda aparecerá em seu lugar no IDE. Caso contrário, uma janela de nível superior separada será criada para tais editores.  
  
  recipiente do subcontexto  
  Um `IVsUserContext` objeto vinculado a um recipiente de contexto. Esse objeto contém palavras-chave de pesquisa, palavras-chave F1 e atributos para uma seleção dentro de um componente IDE. Exemplos de subcontexto incluem um comando em uma janela de ferramentas ou uma palavra-chave em um editor.  
  
  Lista de tarefas  
  Janela de ferramentas implementada pelo IDE e exibe uma lista de tarefas ativas.  
  
  buffer de texto  
  Nome comum do objeto `VSTextBuffer` .  
  
  Exibição de texto  
  Nome comum do objeto `VSTextView` .  
  
  componente de nível superior da ferramenta  
  Um componente que opera como uma janela pop-up sem janelas restritas, coordenando rigidamente a interface do usuário do IDE. Assim como os componentes de nível superior independentes, os componentes de nível superior da ferramenta também devem coordenar os serviços de modalidade e de loop de mensagem com o IDE.  
  
  componente de nível superior  
  Um objeto VSPackage que gerencia uma janela de nível superior não restrita por modelos em vez da área do cliente de uma janela do IDE. Os componentes de nível superior implementam a `IOleComponent` interface para aproveitar os serviços de loop de mensagens, como o acesso ao tempo ocioso.  
  
  IU ativa  
  Um objeto VSPackage que é visível e tem foco no momento.  
  
  Hierarquia da interface do usuário  
  Um objeto COM que implementa a `IVsUIHierarchy` interface para permitir a exibição de uma hierarquia. A janela hierarquia da interface do usuário implementa a `ISelectionContainer` interface para atualizar a janela Propriedades; outras janelas do tipo projeto podem usar essa implementação, se desejado.  
  
  VSCT  
  Tabela de comandos do Visual Studio. O arquivo. vsct contém informações sobre o posicionamento e os comportamentos de menus, barras de ferramentas e comandos no formato XML.  
  
  VSPackage  
  Uma parte do software instalável que estende o IDE do Visual Studio, contribuindo com um ou mais dos seguintes itens: interface do usuário, serviços, tipos de projeto ou Editor/Designer. Um VSPackage consiste em um objeto COM que implementa a `IVsPackage` interface e um ou mais objetos com que implementam outras interfaces para dar suporte à seleção e a outros recursos. Além disso, um VSPackage tem requisitos de registro específicos.
