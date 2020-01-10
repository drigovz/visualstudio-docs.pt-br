---
title: Modele a&#39;arquitetura do seu aplicativo
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- UML, modeling architecture
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba455730ddac9b2a02b8f0580711499d6a779f49
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590222"
---
# <a name="model-your-app39s-architecture"></a>Modele a&#39;arquitetura do seu aplicativo
Para ajudar a garantir que o seu sistema de software ou aplicativo atenda às necessidades de seus usuários, você pode criar modelos no Visual Studio como parte da sua descrição da estrutura geral e do comportamento do seu aplicativo ou sistema de software. Usando modelos, você também pode descrever padrões que são usados em todo o design. Esses modelos ajudam você a entender a arquitetura existente, a discutir alterações e a comunicar suas intenções claramente.

 Para ver quais edições do Visual Studio oferecem suporte a esse recurso, consulte [suporte de edição para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 A finalidade de um modelo é reduzir as ambiguidades que ocorrem nas descrições de idioma natural e ajudar você e seus colegas a visualizar o design e a discutir designs alternativos. Um modelo deve ser usado junto com outros documentos ou discussões. Por si só, um modelo não representa uma especificação completa da arquitetura.

> [!NOTE]
> Ao longo deste tópico, "System" significa o software que você está desenvolvendo. Pode ser uma grande coleção de muitos componentes de software e hardware, ou um único aplicativo ou uma parte de um aplicativo.

 A arquitetura de um sistema pode ser dividida em duas áreas:

- [Design de alto nível](#Structure). Isso descreve os principais componentes e como eles interagem entre si para atender a cada requisito. Se o sistema for grande, cada componente poderá ter seu próprio design de alto nível, que mostra como ele é composto por componentes menores.

- [Padrões de design](#Patterns) e convenções usadas em todos os designs dos componentes. Um padrão descreve uma abordagem específica para atingir uma meta de programação. Usando os mesmos padrões em um design, sua equipe pode reduzir o custo de fazer alterações e desenvolver novos softwares.

## <a name="Structure"></a>Design de alto nível
 Um design de alto nível descreve os principais componentes do seu sistema e como eles interagem entre si para atingir as metas do design. As atividades na lista a seguir estão envolvidas no desenvolvimento do design de alto nível, embora não necessariamente em uma sequência específica.

 Se você estiver atualizando o código existente, poderá começar descrevendo os principais componentes. Verifique se você entendeu as alterações nos requisitos do usuário e depois adicione ou modifique as interações entre os componentes. Se você estiver desenvolvendo um novo sistema, comece compreendendo os principais recursos das necessidades dos usuários. Você pode explorar sequências de interações para os principais casos de uso e, em seguida, consolidar as sequências em um design de componente.

 Em todos os casos, é útil desenvolver as diferentes atividades em paralelo e desenvolver código e testes em um estágio inicial. Evite tentar concluir um desses aspectos antes de iniciar outro. Normalmente, os requisitos e sua compreensão da melhor maneira de criar o sistema serão alterados enquanto você estiver escrevendo e testando o código. Portanto, você deve começar compreendendo e codificando os principais recursos dos requisitos e do seu design. Preencha os detalhes em iterações posteriores do projeto.

- [Noções básicas sobre os requisitos](#Requirements). O ponto de partida de qualquer design é uma compreensão clara das necessidades dos usuários.

- [Padrões de arquitetura](#BigDecisions). As escolhas feitas sobre as principais tecnologias e os elementos arquitetônicos do sistema.

- Modelo de dados dos componentes e interfaces. Você pode desenhar diagramas de classe para descrever as informações que são passadas entre componentes e armazenadas dentro dos componentes.

## <a name="Requirements"></a>Noções básicas sobre os requisitos
 O design de alto nível de um aplicativo completo é desenvolvido com mais eficiência junto com um modelo de requisitos ou outra descrição das necessidades dos usuários. Para obter mais informações sobre modelos de requisitos, consulte [requisitos de usuário de modelo](../modeling/model-user-requirements.md).

 Se o sistema que você está desenvolvendo for um componente em um sistema maior, parte ou todos os seus requisitos poderão ser incorporados em interfaces programáticas.

 O modelo de requisitos fornece essas informações essenciais:

- Interfaces fornecidas. Uma interface fornecida lista os serviços ou operações que o sistema ou componente deve fornecer a seus usuários, sejam usuários humanos ou outros componentes de software.

- Interfaces necessárias. Uma interface necessária lista os serviços ou operações que o sistema ou componente pode usar. Em alguns casos, você poderá criar todos esses serviços como parte do seu próprio sistema. Em outros casos, especialmente se você estiver criando um componente que pode ser combinado com outros componentes em muitas configurações, a interface necessária será definida por considerações externas.

- Requisitos de qualidade de serviço. O desempenho, a segurança, a robustez e outras metas e restrições que o sistema deve atender.

  O modelo de requisitos é escrito a partir do ponto de vista dos usuários do sistema, sejam eles pessoas ou outros componentes de software. Eles não sabem nada do funcionamento interno do seu sistema. Por outro lado, seu objetivo em um modelo de arquitetura é descrever os trabalhos internos e mostrar como eles atendem às necessidades dos usuários.

  Manter os requisitos e modelos de arquitetura separados é útil porque torna mais fácil discutir os requisitos com os usuários. Ele também ajuda a refatorar o design e a considerar as arquiteturas alternativas, mantendo os requisitos inalterados.

  A quantidade de detalhes que você deve colocar em requisitos ou em um modelo de arquitetura depende da escala do projeto e do tamanho e da distribuição da equipe. Uma pequena equipe em um pequeno projeto pode não ultrapassar o esboço de um diagrama de classe dos conceitos de negócios e de alguns padrões de design; um projeto grande distribuído em mais de uma região precisaria de maneira muito mais detalhada.

## <a name="BigDecisions"></a>Padrões de arquitetura
 No início de um desenvolvimento, você precisa escolher as principais tecnologias e elementos dos quais o design depende. As áreas nas quais essas opções devem ser feitas incluem o seguinte:

- Opções de tecnologia base, como a escolha entre um banco de dados e um sistema de arquivos, e a escolha entre um aplicativo em rede e um cliente Web, e assim por diante.

- Opções de estruturas, como uma opção entre Windows Workflow Foundation ou ADO.NET Entity Framework.

- Opções de método de integração, por exemplo, entre um barramento de serviço corporativo ou um canal ponto a ponto.

  Essas opções são frequentemente determinadas pelos requisitos de qualidade de serviço, como escala e flexibilidade, e podem ser feitas antes que os requisitos detalhados sejam conhecidos. Em um sistema grande, a configuração de hardware e software está fortemente relacionada.

  As seleções que você faz afetam a maneira como você usa e interpreta o modelo de arquitetura. Por exemplo, em um sistema que usa um banco de dados, as associações em um diagrama de classe podem representar relações ou chaves estrangeiras no banco de dados, enquanto em um sistema baseado em arquivos XML, as associações podem indicar referências cruzadas que usam XPath. Em um sistema distribuído, as mensagens em um diagrama de sequência podem representar mensagens em uma conexão; em um aplicativo independente, eles podem representar chamadas de função.

## <a name="Patterns"></a>Padrões de design
 Um padrão de design é uma estrutura de tópicos de como criar um aspecto específico do software, especialmente um que se repete em diferentes partes do sistema. Ao adotar uma abordagem uniforme em todo o projeto, você pode reduzir o custo de design, garantir a consistência na interface do usuário e reduzir o custo de entender e alterar o código.

 Alguns padrões de design gerais, como o observador, são bem conhecidos e amplamente aplicáveis. Além disso, há padrões que são aplicáveis apenas ao seu projeto. Por exemplo, em um sistema de vendas na Web, haverá várias operações no código em que as alterações são feitas no pedido de um cliente. Para garantir que o estado do pedido seja exibido com precisão em cada estágio, todas essas operações devem seguir um protocolo específico para atualizar o banco de dados.

 Parte do trabalho da arquitetura de software é determinar quais padrões devem ser adotados em todo o design. Normalmente, essa é uma tarefa em andamento, pois novos padrões e aprimoramentos para padrões existentes serão descobertos à medida que o projeto progride. É útil organizar o plano de desenvolvimento para que você exerça cada um dos seus principais padrões de design em um estágio inicial.

 A maioria dos padrões de design pode ser parcialmente incorporada no código do Framework. Parte do padrão pode ser reduzida para exigir que o desenvolvedor Use classes ou componentes específicos, como uma camada de acesso ao banco de dados que garante que o banco de dados seja manipulado corretamente.

 Um padrão de design é descrito em um documento e normalmente inclui estas partes:

- Nome.

- Descrição do contexto no qual ele é aplicável. Quais critérios devem fazer um desenvolvedor considerar a aplicação desse padrão?

- Breve explicação do problema que ele resolve.

- Modelo das partes principais e suas relações. Elas podem ser classes ou componentes e interfaces, com associações e dependências entre eles. Os elementos geralmente se enquadram em duas categorias:

- Convenções de nomenclatura.

- Descrição de como o padrão resolve o problema.

- Descrição das variações que os desenvolvedores podem adotar.

## <a name="see-also"></a>Veja também

- [Visualizar código](../modeling/visualize-code.md)
- [Requisitos de usuário do modelo](../modeling/model-user-requirements.md)
- [Desenvolver testes por meio de um modelo](../modeling/develop-tests-from-a-model.md)
- [Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)
