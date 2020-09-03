---
title: Estereótipos padrão para modelos UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, stereotypes
- UML diagrams, stereotypes
ms.assetid: 8a8c2321-1cae-4ba8-bb9e-23495c3404d8
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a16c68b3b14be57fb0a6a45c740e5420a82c2ddf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661046"
---
# <a name="standard-stereotypes-for-uml-models"></a>Estereótipos padrão para modelos UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode adicionar estereótipos a elementos de modelo UML para fornecer informações adicionais para o leitor ou para processamento de máquina. Os estereótipos são definidos em perfis e cada perfil fornece um conjunto de estereótipos. Vários perfis são fornecidos com o Visual Studio. Você também pode definir seus próprios perfis que podem conter seus próprios estereótipos. Para obter mais informações, consulte [definir um perfil para estender o UML](../modeling/define-a-profile-to-extend-uml.md).

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="the-standard-profiles"></a>Os perfis padrão
 Os perfis a seguir estão disponíveis em uma edição com suporte do Visual Studio assim que você o tiver instalado.

|Perfil|Finalidade|
|-------------|-------------|
|[L2 de perfil padrão UML](#L2)|Um conjunto padrão de estereótipos que pode ser usado para adicionar informações extras sobre um elemento ou uma relação.|
|[Perfil padrão de UML L3](#L3)|Um conjunto padrão de estereótipos que pode ser usado para adicionar informações extras sobre um elemento ou uma relação.|
|[Perfil C#](#NetProfile)|Se você pretender uma classe ou outro elemento em um modelo UML para representar o código do programa, poderá indicar isso aplicando um dos estereótipos do perfil do C#.<br /><br /> Esses estereótipos também adicionam Propriedades aos elementos do modelo.|

 Quando você cria um novo modelo UML, os perfis padrão UML L2 e L3 são vinculados ao modelo, a menos que você remova os links.

 Para usar os estereótipos em qualquer um desses perfis, primeiro você deve vincular o perfil a um pacote ou a um modelo que contém os elementos aos quais você deseja aplicá-los.

#### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Para vincular um perfil a um modelo ou pacote

1. Abra o **Gerenciador de modelos UML**. No menu **arquitetura** , aponte para **Windows**e clique em Gerenciador de **modelos UML**.

2. Localize um pacote ou um modelo que contenha todos os elementos aos quais você deseja aplicar os estereótipos no perfil.

3. Clique com o botão direito do mouse no pacote ou no modelo e clique em **Propriedades**.

4. Na janela **Propriedades** , defina a propriedade **perfis** para os perfis desejados.

#### <a name="to-remove-the-link-between-a-profile-and-a-model-or-package"></a>Para remover o link entre um perfil e um modelo ou pacote

1. No Gerenciador de modelos UML, clique com o botão direito do mouse no modelo ou pacote e clique em **Propriedades**.

2. No janela Propriedades, defina a propriedade **Profiles** como Empty.

    > [!NOTE]
    > Você pode desvincular um perfil somente se nenhum dos elementos no modelo ou pacote usar estereótipos desse perfil.

#### <a name="to-apply-a-stereotype-to-a-model-element"></a>Para aplicar um estereótipo a um elemento de modelo

1. Clique com o botão direito do mouse no elemento de modelo em um diagrama ou em **Gerenciador de modelos UML**e clique em **Propriedades**.

2. Clique na propriedade **estereótipos** e selecione os estereótipos que você deseja aplicar.

     Os estereótipos selecionados aparecem dentro de «divisas» no elemento Model, para a maioria dos tipos de elemento.

    > [!NOTE]
    > Se você não puder ver a propriedade **estereótipos** ou se o estereótipo desejado não for exibido, verifique se o elemento de modelo está dentro de um pacote ou um modelo ao qual o perfil apropriado foi vinculado.

3. Alguns estereótipos permitem que você defina os valores de propriedades adicionais para o elemento de modelo. Para ver essas propriedades, expanda a propriedade **estereótipos** .

### <a name="uml-standard-profile-l2"></a><a name="L2"></a> L2 de perfil padrão UML
 Os estereótipos a seguir podem ser usados para especializar o significado dos elementos de modelo UML, a menos que o link para o perfil tenha sido removido do modelo.

 O significado exato desses estereótipos é determinado por suas próprias convenções locais e por qualquer ferramenta que você possa usar para processar o modelo.

|Estereótipo|Aplica-se a|Significado|
|----------------|----------------|-------------|
|auxiliar|Classe|Uma classe que dá suporte a outra classe, normalmente Implementando lógica adicional. A outra classe pode ter o estereótipo «Focus».|
|chamada|Dependência|A classe de cliente chama as operações do fornecedor.|
|create|Dependência|A classe de cliente cria instâncias do fornecedor.|
|create|Mensagem|O remetente cria o receptor.|
|create|Operação|Esta operação é um construtor.|
|origina|Dependência|O elemento do cliente é completamente computado ou parcialmente do fornecedor.|
|destroy|Operação|A operação destrói sua instância.|
|documento|Artefato|Um «arquivo» que não é uma origem ou um executável.|
|entidade|Componente|O componente representa um conceito de negócios.|
|executável|Artefato|Um executável «arquivo».|
|file|Artefato|Um arquivo físico.|
|foco|Classe|Uma classe que define a lógica de negócios principal, que é suportada por várias classes «auxiliar».|
|estrutura|Pacote|Esse pacote define um padrão de design reutilizável.|
|implementar|Componente|A implementação de uma «especificação».|
|implementationClass|Classe|A classe descreve uma implementação e cada instância de tempo de execução tem uma classe de implementação fixa. Contraste com «tipo».|
|instanciar|Dependência|O cliente cria instâncias do fornecedor.|
|biblioteca|Artefato|Uma biblioteca «arquivo».|
|metaclass|Classe|As instâncias dessa classe também são classes.|
|modelLibrary|Pacote|Contém elementos de modelo destinados a serem reutilizados pela importação de pacotes. Normalmente definido como parte de um perfil e importado automaticamente pelo aplicativo do perfil.|
|process|Componente|Um componente baseado em transação ou um que transporta um thread.|
|percepção|Classe, interface, componente|Descreve uma implementação.|
|restringir|Dependência|A classe, o componente ou o pacote de cliente fornece mais informações sobre a especificação ou o design do fornecedor.|
|responsabilidade|Dependência|O comentário na extremidade do fornecedor da dependência define as responsabilidades da classe ou do componente do cliente.|
|Script|Artefato|Um «arquivo "interpretável».|
|Enviar|Dependência|A operação de origem envia o sinal de destino.|
|serviço|Componente|Um componente sem estado.|
|source|Artefato|Um «arquivo» compilável.|
|especificação|Classe, interface, componente|Define o comportamento de um componente ou objeto sem definir como ele funciona internamente.|
|subsystem|Componente|Uma parte de um sistema grande. Um subsistema em um diagrama de caso de uso é um componente com o estereótipo do subsistema.|
|rastreamento|Dependência|O elemento Client faz parte do design que percebe o fornecedor. As duas extremidades dessa dependência normalmente estão em modelos diferentes. Um desses modelos é uma realização do outro.|
|tipo|Classe|Especifica o comportamento de um objeto sem informando como ele é implementado. Um objeto é um membro de um tipo se estiver em conformidade com a especificação.|
|utilitário|Classe|Uma coleção de funções estáticas. A classe não tem nenhuma instância.|

### <a name="uml-standard-profile-l3"></a><a name="L3"></a> Perfil padrão de UML L3
 Os estereótipos a seguir podem ser usados para especializar o significado dos elementos de modelo UML, a menos que o perfil tenha sido desvinculado do modelo.

 O significado exato desses estereótipos é determinado por suas próprias convenções locais e por qualquer ferramenta que você possa usar para processar o modelo.

|Estereótipo|Aplica-se a|Descrição|
|----------------|----------------|-----------------|
|buildComponent|Componente|Uma coleção de elementos usados para definir uma compilação.|
|metaModel|Modelo|Define uma linguagem de modelagem, como uma variante de UML, ou uma linguagem específica de domínio.|
|systemModel|Modelo|Um modelo que é uma coleção de modelos que se aplicam ao mesmo sistema, por exemplo, uma especificação, uma realização e relações de rastreamento entre eles.|

## <a name="c-profile"></a><a name="NetProfile"></a> Perfil C#
 Os estereótipos definidos neste perfil permitem que você indique que um elemento de modelo destina-se à tradução para o código do programa. Cada estereótipo define propriedades adicionais que podem ser definidas no elemento Model.

 Para disponibilizar esses estereótipos, vincule um modelo ou pacote ao perfil do C#. Em seguida, você pode aplicar os estereótipos a elementos de modelo nesse modelo ou pacote.

 Os estereótipos disponíveis, os elementos aos quais eles se aplicam e as propriedades adicionais que eles tornam disponíveis são resumidos na tabela a seguir.

|Estereótipo|Aplica-se a|Propriedades|
|----------------|----------------|----------------|
|**Classe C#**|Classe UML<br /><br /> Componente|**Atributos CLR**<br /><br /> **Is Partial**<br /><br /> **Está lacrado**<br /><br /> **Is Static**<br /><br /> **Is Unsafe**<br /><br /> **Visibilidade do pacote**|
|**Struct do C#**|Classe UML<br /><br /> Componente|**Atributos CLR**<br /><br /> **Is Partial**<br /><br /> **Is Unsafe**<br /><br /> **Visibilidade do pacote**|
|**Membros globais do C#**|Classe UML<br /><br /> Componente|**Atributos CLR**|
|**Interface C#**|Interface UML|**Atributos CLR**<br /><br /> **Is Partial**<br /><br /> **Visibilidade do pacote**|
|**Enum do C#**|Enumeração UML|**ClrAttributes**<br /><br /> **Tipo base**|
|**Namespace C#**|Pacote UML|**Atributos CLR**<br /><br /> **Nome base**<br /><br /> **Usar namespaces**|

## <a name="see-also"></a>Consulte Também
 [Adicionar estereótipos a elementos de modelo UML](../modeling/add-stereotypes-to-uml-model-elements.md) [Personalize seu modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [defina um perfil para estender o UML](../modeling/define-a-profile-to-extend-uml.md)
