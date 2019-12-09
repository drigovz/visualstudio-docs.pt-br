---
title: Gerenciar modelos e diagramas sob controle de versão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- models, version control
ms.assetid: ca6443e3-6d11-4da8-aae7-ca7dcc410076
caps.latest.revision: 32
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30b13610cc59b8a0225e52abf47f9a4f2cc97d1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657575"
---
# <a name="manage-models-and-diagrams-under-version-control"></a>Gerenciar modelos e diagramas com controle de versão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gerencie versões diferentes de seus projetos de modelagem e diagramas, incluindo mapas de código (arquivos. dgml) usando o [controle de versão do Team Foundation ou git](https://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314); com o Team Foundation Server local ou na nuvem com Visual Studio Team Services.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!IMPORTANT]
> Tenha cuidado quando vários usuários trabalham no mesmo projeto de modelagem. Descubra como você pode [organizar modelos em projetos médios ou grandes](../modeling/structure-your-modeling-solution.md).

## <a name="ModelingProjects"></a>Arquivos em um projeto de modelagem
 Mais de um usuário pode trabalhar em um projeto de modelagem ao mesmo tempo, desde que eles trabalhem em arquivos diferentes.

 Para evitar ou resolver conflitos entre as alterações feitas por diferentes usuários, é importante entender como o modelo é armazenado em arquivos.

- Cada pacote é armazenado em um arquivo **. Uml** separado, que é mantido na pasta do projeto **ModelDefinition** . O modelo também tem um arquivo **. Uml** . Se um desses arquivos for excluído ou corrompido, o pacote ou modelo correspondente será perdido.

- Cada diagrama é armazenado em dois arquivos. Por exemplo, um diagrama de classe tem:

  - **DiagramName. classdiagram** -se esse arquivo for excluído ou corrompido, o diagrama será perdido, mas as classes e associações que ele mostrou ainda estarão no modelo e poderão ser vistas no Gerenciador de modelos UML.

  - **DiagramName. classdiagram. layout** – se esse arquivo for excluído, as formas ainda aparecerão no diagrama, mas perderão seus tamanhos e posições. Cada arquivo de layout é subsidiário para um arquivo de diagrama. Para vê-lo, clique no [+] ao lado do arquivo de diagrama em Gerenciador de Soluções.

> [!NOTE]
> É importante manter a consistência entre os arquivos. Por exemplo, se você usar o controle do código-fonte para reverter alterações em um arquivo. UML, deverá reverter as alterações correspondentes no diagrama. * e nos arquivos. layout ao mesmo tempo. Elementos representados em um. \*diagram arquivo será perdido se eles não forem também representados em um arquivo. Uml.

## <a name="Shared"></a>Trabalhando em projetos de modelagem compartilhados
 Para minimizar os conflitos entre o trabalho simultâneo em diferentes partes de um projeto:

- Divida seu projeto de modelagem em pacotes que representam áreas de trabalho diferentes. Mova todo o modelo para os pacotes, em vez de deixá-lo no modelo raiz. Para obter mais informações, consulte [definir pacotes e namespaces](../modeling/define-packages-and-namespaces.md).

- Usuários diferentes não devem trabalhar no mesmo pacote ou diagrama ao mesmo tempo.

- Se você estiver usando perfis, certifique-se de que todos tenham instalado os mesmos perfis. Consulte [personalizar seu modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md).

- Para ajudar a garantir que você altere apenas o pacote no qual está trabalhando:

  - Defina a propriedade **LinkedPackage** de uma classe UML, um componente ou um diagrama de caso de uso.

  - No Gerenciador de modelos UML, arraste uma atividade ou interação para seu pacote assim que você criá-la. Esse elemento aparecerá no Gerenciador de modelos UML quando você criar o primeiro nó na atividade ou no diagrama de sequência.

- Para ajudá-lo a acompanhar os pacotes, renomeie os arquivos de pacote para refletir os nomes de pacote reais.

- Em [!INCLUDE[esprscc](../includes/esprscc-md.md)], sempre faça **check-in** e obtenha as operações de **versão mais recentes** no projeto de modelagem completo, nunca em arquivos individuais.

- Sempre execute uma operação **Get** imediatamente antes de fazer check-in no projeto de modelagem.

- Sempre feche todos os diagramas antes de executar uma operação **Get** .

    > [!NOTE]
    > Se um arquivo estiver aberto quando você executar um **Get**, e a operação resultar em alterações locais, será solicitado que você recarregue o arquivo. Nesse caso, clique em **não**e recarregue o projeto completo. Em **Gerenciador de soluções**, clique com o botão direito do mouse no nó projeto de modelagem, clique em **descarregar projeto**e, em seguida, clique em **recarregar projeto**.

### <a name="Exclusive"></a>Alterações que exigem acesso exclusivo ao modelo
 Antes de fazer os seguintes tipos de alterações, verifique se você tem um bloqueio de check-out no projeto inteiro.

- Renomear ou excluir elementos que são referenciados de outros pacotes.

- Alterar propriedades de relações que cruzam os limites do pacote.

- Para saber mais sobre bloqueios de check-out, consulte [fazer check-out e editar arquivos](https://msdn.microsoft.com/library/eb404d63-c448-4994-9416-3e6d50ec554a).

##### <a name="to-move-a-diagram-file-in-or-out-of-a-project-folder"></a>Para mover um arquivo de diagrama para dentro ou para fora de uma pasta de projeto

1. Inicie o **prompt de comando do desenvolvedor para o Visual Studio**.

2. Use **tf rename** para mover o arquivo de diagrama e seu arquivo **. layout** :

     `tf rename sourcePath targetPath`

3. Em Gerenciador de Soluções, clique com o botão direito do mouse no arquivo e clique em **excluir do projeto**.

4. Adicione o arquivo à pasta de destino.

     Em Gerenciador de Soluções, clique com o botão direito do mouse na pasta de destino ou no projeto, aponte para **Adicionar**e clique em **Item existente**. Na caixa de diálogo, selecione o arquivo de diagrama e clique em **Adicionar**. O arquivo de layout será adicionado automaticamente.

    > [!NOTE]
    > Não é possível mover o arquivo para um projeto diferente.

## <a name="Merging"></a>Mesclando alterações em diagramas e arquivos de modelo
 Depois que mais de um usuário tiver trabalhado em um modelo simultaneamente, [!INCLUDE[esprscc](../includes/esprscc-md.md)] solicitará que você mescle as alterações nos arquivos de modelo. Trabalhar em projetos separados, conforme descrito nas seções anteriores anterior, evitará a maioria das mesclagens. Normalmente, os conflitos restantes podem ser mesclados com segurança automaticamente. Os seguintes tipos de alterações não devem causar dificuldade:

- Tipos de linhas de vida. Quando você adiciona uma linha de vida a uma interação (diagrama de sequência), seu tipo é armazenado no modelo raiz, a menos que você tenha criado a linha da vida a partir de um tipo existente.

- Novas atividades e interações são inicialmente armazenadas no modelo raiz.

- Adicionando elementos e relações.

- Renomear ou excluir elementos que são referenciados somente dentro de seu próprio pacote.

## <a name="see-also"></a>Consulte também
 [Analisando e modelando a arquitetura](../modeling/analyze-and-model-your-architecture.md) [compartilhar modelos e exportar diagramas](../modeling/share-models-and-exporting-diagrams.md)
