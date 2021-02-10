---
title: Criando um modelo de conectividade de dados corporativos | Microsoft Docs
description: Criar um modelo de BDC (conectividade de dados corporativos). Adicione entidades e métodos. Defina os parâmetros do método. Adicionar descritores de filtro. Valide o modelo BDC.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], designing a model
- Business Data Connectivity service [SharePoint development in Visual Studio], designing a model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8fb1aa194688533855b7c5bd1d58a4e3b97ac749
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948836"
---
# <a name="design-a-business-data-connectivity-model"></a>Criar um modelo de conectividade de dados corporativos
  Você pode desenvolver um modelo para o serviço corporativo de conectividade de dados (BDC) adicionando entidades e métodos a um arquivo de modelo. Uma entidade descreve uma coleção de campos de dados. Por exemplo, uma entidade pode representar uma tabela em um banco de dados. Um método executa uma tarefa como adicionar, excluir ou atualizar dados representados pelas entidades. Para obter mais informações, consulte [integrar dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).

## <a name="add-entities"></a>Adicionar entidades
 Você pode adicionar uma entidade arrastando ou copiando uma **entidade** da caixa de **ferramentas** do Visual Studio para o BDC designer. Para obter mais informações, consulte [como: adicionar uma entidade a um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md).

 Defina os campos da entidade em uma classe. Por exemplo, você pode adicionar um campo chamado `Address` a uma `Customer` classe. Você pode adicionar uma nova classe ao projeto ou usar uma classe existente criada usando outras ferramentas, como o Object Relational Designer (O/R Designer). O nome da entidade e o nome da classe que representa a entidade não precisam corresponder. Você relaciona a classe à entidade ao definir os métodos em seu modelo.

## <a name="add-methods"></a>Adicionar métodos
 O serviço do BDC chama métodos em seu modelo quando os usuários exibem, adicionam, atualizam ou excluem informações em uma lista ou Web Part que se baseia em seu modelo. Você deve adicionar um método ao modelo para cada tarefa que o usuário pode executar. Crie métodos selecionando qualquer um dos cinco tipos de método básicos da janela **detalhes do método do BDC** . A tabela a seguir descreve os cinco métodos básicos de um modelo BDC.

|Método|Descrição|
|------------|-----------------|
|Localizado|Retorna uma coleção de instâncias de entidade. Chamado quando o usuário abre a lista ou Web Part. Para obter mais informações, consulte [como adicionar um método localizador](../sharepoint/how-to-add-a-finder-method.md).|
|Localizador Específico|Retorna uma instância de entidade específica. Chamado quando um usuário exibe os detalhes de um item específico em uma lista. Para obter mais informações, consulte [como adicionar um método localizador específico](../sharepoint/how-to-add-a-specific-finder-method.md).|
|Criador|Adiciona novos dados à fonte de dados de uma entidade. Chamado quando os usuários escolhem o botão **novo item** na faixa de faixas de uma lista com base no modelo. Para obter mais informações, consulte [como: adicionar um método de criador](../sharepoint/how-to-add-a-creator-method.md).|
|Atualizador|Modifica os dados em uma lista. Chamado quando os usuários atualizam as informações em uma lista. Para obter mais informações, consulte [como adicionar um método de atualizador](../sharepoint/how-to-add-an-updater-method.md).|
|Excluir|Remove dados. Chamado quando os usuários excluem um item da lista. Para obter mais informações, consulte [como: adicionar um método excluidor](../sharepoint/how-to-add-a-deleter-method.md).|

## <a name="define-method-parameters"></a>Definir parâmetros do método
 Quando você cria um método, o Visual Studio adiciona os parâmetros de entrada e saída apropriados para o tipo de método. Esses parâmetros são apenas espaços reservados. Na maioria dos casos, você deve modificar os parâmetros para que eles passem ou retornem o tipo correto de dados. Por exemplo, por padrão, um método Finder retorna uma cadeia de caracteres. Na maioria dos casos, você deseja modificar o parâmetro de retorno do método Finder para que ele retorne uma coleção de entidades. Você pode fazer isso modificando o descritor de tipo do parâmetro. Um descritor de tipo é uma coleção de atributos que descreve o tipo de dados de um parâmetro. Para obter mais informações, consulte [como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 O Visual Studio permite que você copie os descritores de tipo entre os parâmetros no modelo. Por exemplo, você pode definir um descritor de tipo chamado `CustomerTD` para o parâmetro de retorno do `GetCustomer` método. Você pode copiar o `CustomerTD` descritor de tipo no **Gerenciador do BDC** e, em seguida, colar esse descritor de tipo no parâmetro de entrada do `CreateCustomer` método. Isso impede que você precise definir o mesmo descritor de tipo mais de uma vez.

## <a name="method-instances"></a>Instâncias de método
 Quando você cria um método, o Visual Studio adiciona uma instância de método padrão. Uma instância de método é uma referência a um método, mais os valores padrão para os parâmetros. Um único método pode ter várias instâncias de método. Cada instância é uma combinação da assinatura do método e de um conjunto de valores padrão. Para obter mais informações, consulte [como: definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

 Quando você executa o projeto, as instâncias de método aparecem em uma lista suspensa acima da lista do SharePoint. Os usuários podem escolher instâncias de método para exibir os dados.

 Para adicionar valores padrão à instância do método, você precisa modificar o XML do modelo diretamente. Para obter mais informações, consulte [DefaultValue](/previous-versions/office/developer/sharepoint-2010/ee559319(v=office.14)).

## <a name="add-filter-descriptors"></a>Adicionar descritores de filtro
 Os consumidores do modelo podem querer recuperar instâncias de uma entidade que correspondam a alguns critérios. Para habilitar essa funcionalidade, você pode adicionar um descritor de filtro a um método. Os descritores de filtro permitem que os consumidores de modelo filtrem conjuntos de resultados de método passando valores para métodos antes de serem executados. Para obter mais informações, consulte [como: adicionar parâmetros de filtro a operações para limitar instâncias do sistema externo](/previous-versions/office/developer/sharepoint-2010/ee554889(v=office.14)).

 O SharePoint fornece vários recursos que permitem aos usuários fornecer valores de filtro. Por exemplo, Web Parts de dados corporativos fornecem uma caixa de texto de filtro. Os usuários podem limitar os dados em uma lista inserindo um valor na caixa de texto. Para obter mais informações sobre como adicionar um descritor de filtro a um método, consulte [como: adicionar um descritor de filtro a um método localizador](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

### <a name="filter-descriptor-properties"></a>Propriedades do descritor de filtro
 Você deve definir o valor do **descritor de tipo**, **nome** e propriedades de **tipo** associados de um descritor de filtro. Todas as outras propriedades são opcionais.

 A propriedade do **descritor de tipo associada** relaciona o descritor de filtro a um parâmetro de entrada. Quando um usuário fornece um valor de filtro, o serviço do BDC passa esse valor para o método usando o parâmetro de entrada.

 A propriedade **Type** descreve o padrão de filtragem que você deseja usar. No SharePoint, o padrão de filtragem que você seleciona afeta o texto que aparece na interface do usuário. Por exemplo, para um padrão de filtragem de comparador, o texto **é igual a** aparece como um controle acima de uma Web Part de dados corporativos. Para obter mais informações sobre cada padrão de filtragem, consulte [tipos de filtros com suporte pelo BDC](/previous-versions/office/developer/sharepoint-2010/ee556392(v=office.14)).

 Para obter mais informações sobre as propriedades de um descritor de filtro, consulte [FilterDescriptor](/previous-versions/office/developer/sharepoint-2010/ee557835(v=office.14)).

### <a name="provide-default-values"></a>Fornecer valores padrão
 Em alguns casos, o usuário pode não fornecer um valor de filtro. Você pode fornecer um valor padrão adicionando um valor padrão à instância do método ou definindo o valor padrão no código do seu método. Para obter mais informações sobre como adicionar um valor padrão à instância do método, consulte [MethodInstance](/previous-versions/office/developer/sharepoint-2010/ee556838(v=office.14)). Para obter um exemplo de como definir o valor padrão de um parâmetro de entrada no código do seu método, consulte [como: adicionar um descritor de filtro a um método localizador](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).

## <a name="validate-the-model"></a>Validar o modelo
 Você pode validar seu modelo durante o desenvolvimento. O Visual Studio identifica problemas que podem impedir que seu modelo se comportar conforme o esperado. Esses problemas aparecem no **lista de erros** do Visual Studio.

 Você pode validar um modelo abrindo o menu de atalho para o BDC designer e, em seguida, escolhendo **validar**. Se o modelo contiver erros, eles aparecerão na **lista de erros**. Você pode mover rapidamente o cursor para o código que contém um erro clicando duas vezes no erro na lista. Como alternativa, você pode escolher as teclas **F8** ou **Shift** + **F8** repetidamente para avançar ou retroceder os erros na lista.

 Os erros de validação podem ocorrer quando as regras do modelo são violadas de alguma forma. Por exemplo, se a propriedade **IsCollection** de um descritor de tipo for definida como **true**, mas não existir nenhum descritor de tipo filho, um erro de validação será exibido. Talvez seja necessário consultar as regras de um modelo BDC para entender alguns erros que aparecem no **lista de erros** do Visual Studio. Para obter mais informações sobre as regras de um modelo BDC, consulte [BdcMetadata Schema](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="debug-the-solution-that-contains-the-model"></a>Depurar a solução que contém o modelo
 Você pode depurar seu código da mesma forma que depuraria qualquer código no Visual Studio. Para depurar seu código, defina pontos de interrupção em qualquer lugar no código e inicie o depurador. O Visual Studio abre o site do SharePoint. No SharePoint, crie uma lista ou Web Part que usa seus dados corporativos. Em seguida, você pode percorrer seu código. Para obter mais informações sobre como depurar projetos do SharePoint, consulte [solução de problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

 Você também pode depurar o código em assemblies personalizados que você adiciona ao projeto. No entanto, para depurar o código em um assembly personalizado, você deve adicionar o assembly ao pacote de solução. Para obter mais informações, consulte [como adicionar e remover assemblies adicionais](../sharepoint/how-to-add-and-remove-additional-assemblies.md).

 Para obter mais informações sobre como adicionar um assembly personalizado ao seu projeto, consulte [como incluir um assembly personalizado em um recurso do BDC](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).

### <a name="configure-bdc-security"></a>Configurar a segurança do BDC
 Talvez você precise modificar suas configurações de segurança no SharePoint antes de poder depurar sua solução. Para modificar essas configurações, abra o aplicativo de serviço de conectividade de dados corporativos no site da administração central do SharePoint 2010. Na caixa de diálogo **definir permissões de armazenamento de metadados** , adicione sua conta de usuário e, em seguida, selecione uma das seguintes opções:

|Tarefa|Opção|
|----------|------------|
|Para implantar modelos no serviço BDC.|Editar|
|Para criar listas e Web Parts usando tipos de conteúdo externo (entidades) em seu modelo.|Selecionável em clientes|
|Para criar, ler, atualizar e excluir dados de entidade.|Execute (executar)|

 Para obter mais informações sobre essas configurações, consulte [Gerenciamento de serviços de conectividade de dados corporativos](/previous-versions/office/sharepoint-server-2010/ee661742(v=office.14)).

 Você também pode definir permissões de segurança para modelos individuais ou tipos de conteúdo externo. Para obter mais informações sobre como definir as permissões de segurança de um modelo, consulte [Gerenciamento de modelo do BDC](/previous-versions/office/sharepoint-server-2010/ee524073(v=office.14)). Para obter mais informações sobre como definir as permissões de segurança de um tipo de conteúdo externo, consulte [Gerenciamento de tipo de conteúdo externo](/previous-versions/office/sharepoint-server-2010/ee524076(v=office.14)).

> [!NOTE]
> Use essas configurações para depurar uma solução no servidor do SharePoint local. Para obter mais informações sobre como definir as configurações de segurança relacionadas ao BDC no SharePoint Server de produção, consulte [visão geral de segurança dos serviços de conectividade de dados corporativos](/previous-versions/office/sharepoint-server-2010/ee661743(v=office.14)).

### <a name="retract-models-that-become-corrupt"></a>Cancelar modelos que se tornam corrompidos
 Na primeira vez que você iniciar o depurador, o Visual Studio implantará todo o modelo no SharePoint. Para cada vez depois, o Visual Studio atualiza o modelo no SharePoint com as alterações feitas entre as implantações.

 Pode haver situações em que você queira que o Visual Studio retraia o modelo do SharePoint completamente. Por exemplo, um modelo pode ser corrompido.  Para reimplantar o modelo no SharePoint, defina a propriedade **atualização incremental** do modelo como **false** e, em seguida, inicie o depurador. A propriedade **atualização incremental** aparece na janela **Propriedades** quando você seleciona o nó que representa o modelo no **BDC Explorer**. Por padrão, o nome do modelo é **BdcModel1**.

### <a name="change-identifier-names-of-entities-in-the-model"></a>Alterar nomes de identificador de entidades no modelo
 Se você alterar o nome de um identificador depois de implantar o modelo, você poderá receber um erro de implantação. Não é possível resolver esse erro definindo a propriedade de **atualização incremental** do modelo como **false**. Você deve retrair o modelo manualmente e, em seguida, implantar a solução novamente. Para obter mais informações, consulte [solução de problemas de soluções do SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md). Você pode evitar esse erro definindo a propriedade de **atualização incremental** como **false** antes de implantar inicialmente o modelo.

## <a name="locate-documentation-for-bdc-model-elements"></a>Localizar a documentação dos elementos de modelo do BDC
 O Visual Studio adiciona um elemento XML ao modelo para cada entidade, método ou outro item que você criar. Os atributos do elemento aparecem como propriedades na janela **Propriedades** . Para obter informações sobre os elementos e atributos que o Visual Studio gera conforme você cria o modelo, consulte [esquema BdcMetadata](/previous-versions/office/developer/sharepoint-2010/ee556387(v=office.14)).

## <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Visão geral das ferramentas de design de modelo do BDC](../sharepoint/bdc-model-design-tools-overview.md)|Descreve as ferramentas que você pode usar para criar visualmente um modelo para o BDC.|
|[Como: adicionar uma entidade a um modelo](../sharepoint/how-to-add-an-entity-to-a-model.md)|Mostra como adicionar tipos de conteúdo externo, ou entidades, ao modelo.|
|[Como adicionar um método localizador](../sharepoint/how-to-add-a-finder-method.md)|Mostra como adicionar um método que permite aos usuários exibir uma lista de entidades em uma lista ou Web Part.|
|[Como adicionar um método localizador específico](../sharepoint/how-to-add-a-specific-finder-method.md)|Mostra como adicionar um método que permite aos usuários exibir os detalhes de uma entidade específica.|
|[Como: adicionar um método de criador](../sharepoint/how-to-add-a-creator-method.md)|Mostra como adicionar um método que permite aos usuários adicionar registros a uma fonte de dados diretamente de uma lista ou Web Part.|
|[Como adicionar um método excluidor](../sharepoint/how-to-add-a-deleter-method.md)|Mostra como adicionar um método que permite aos usuários remover dados de uma fonte de dados usando as opções da interface do usuário de uma lista ou Web Part.|
|[Como adicionar um método de atualizador](../sharepoint/how-to-add-an-updater-method.md)|Mostra como adicionar um método que permite aos usuários alterar os registros de dados em uma fonte de dados diretamente de uma lista ou Web Part.|
|[Como: adicionar um parâmetro a um método](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Mostra como usar a janela detalhes do método no Visual Studio para adicionar parâmetros de entrada e de retorno a um método.|
|[Como definir o descritor de tipo de um parâmetro](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Mostra como definir tipos de dados de parâmetro no modelo.|
|[Como definir uma instância de método](../sharepoint/how-to-define-a-method-instance.md)|Mostra como criar uma instância de um método que o BDC executa.|
|[Como: adicionar um descritor de filtro a um método localizador](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Mostra como permitir que os usuários limitem o número de instâncias retornadas por um método localizador.|
|[Criando uma associação entre entidades](../sharepoint/creating-an-association-between-entities.md)|Descreve como você pode definir relações entre entidades no modelo. Os dados de negócios Web Parts, listas externas e aplicativos personalizados podem exibir essas relações de dados em uma interface do usuário.|
|[Como: criar uma associação entre entidades](../sharepoint/how-to-create-an-association-between-entities.md)|Mostra como definir relações entre entidades no modelo.|
|[Walkthrough: lista de Createan externa no SharePoint usando dados corporativos](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Fornece instruções passo a passo que mostram como criar e testar um modelo que exibe contatos em uma lista externa do SharePoint.|
|[Integre dados corporativos ao SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Fornece uma visão geral de como criar e criar modelos para o serviço BDC.|
