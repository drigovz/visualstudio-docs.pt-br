---
title: Solucionando problemas de referências de serviço | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60f06aa64cf6a6b96f0c4d610fba1d20b794c55f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667209"
---
# <a name="troubleshooting-service-references"></a>Solucionando problemas de referências de serviço
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Este tópico lista os problemas comuns que podem ocorrer quando você está trabalhando com referências de [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] ou [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] no [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

## <a name="error-returning-data-from-a-service"></a>Erro ao retornar dados de um serviço
 Quando você retorna um `DataSet` ou `DataTable` de um serviço, você pode receber uma exceção "a cota de tamanho máximo para mensagens de entrada foi excedida". Por padrão, a propriedade `MaxReceivedMessageSize` para algumas associações é definida com um valor relativamente pequeno para limitar a exposição a ataques de negação de serviço. Você pode aumentar esse valor para evitar a exceção.

 Para corrigir esse erro:

1. Em **Gerenciador de soluções**, clique duas vezes no arquivo app. config para abri-lo.

2. Localize a propriedade `MaxReceivedMessageSize` e altere-a para um valor maior.

## <a name="cannot-find-a-service-in-my-solution"></a>Não é possível encontrar um serviço em minha solução
 Quando você clica no botão **descobrir** na caixa de diálogo **Adicionar referências de serviço** , um ou mais projetos de biblioteca de serviço WCF na solução não aparecem na lista de serviços. Isso pode ocorrer se uma biblioteca de serviço tiver sido adicionada à solução, mas ainda não tiver sido compilada.

 Para corrigir esse erro:

- Em **Gerenciador de soluções**, clique com o botão direito do mouse no projeto da biblioteca de serviço WCF e clique em **Compilar**.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Erro ao acessar um serviço por meio de um Área de Trabalho Remota
 Quando um usuário acessa um serviço WCF hospedado na Web por uma conexão de área de trabalho remota e o usuário não tem permissões administrativas, a autenticação NTLM é usada. Se o usuário não tiver permissões administrativas, o usuário poderá receber a seguinte mensagem de erro: "a solicitação HTTP não está autorizada com o esquema de autenticação de cliente ' anônimo '. O cabeçalho de autenticação recebido do servidor era ' NTLM '. "

 Para corrigir esse erro:

1. No projeto de site, abra as páginas de **Propriedades** .

2. Na guia **Opções de início** , desmarque a caixa de seleção **autenticação NTLM** .

    > [!NOTE]
    > Você deve desativar a autenticação NTLM somente para sites que contenham exclusivamente serviços WCF. A segurança para serviços WCF é gerenciada por meio da configuração no arquivo Web. config. Isso torna a autenticação NTLM desnecessária.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>O nível de acesso para a configuração de classes geradas não tem nenhum efeito
 Definir a opção **nível de acesso para classes geradas** na caixa de diálogo **Configurar referências de serviço** como **interno** ou **Friend** nem sempre funcionará. Embora a opção pareça estar definida na caixa de diálogo, as classes de suporte resultantes serão geradas com um nível de acesso de `Public`.

 Essa é uma limitação conhecida de determinados tipos, como aqueles serializados usando o <xref:System.Xml.Serialization.XmlSerializer>.

## <a name="error-debugging-service-code"></a>Erro ao depurar código de serviço
 Ao entrar no código de um serviço WCF do código do cliente, você poderá receber um erro relacionado a símbolos ausentes. Isso pode ocorrer quando um serviço que era parte de sua solução foi movido ou removido da solução.

 Quando você adiciona pela primeira vez uma referência a um serviço WCF que faz parte da solução atual, uma dependência de compilação explícita é adicionada entre o projeto de serviço e o projeto de cliente de serviço. Isso garante que o cliente sempre acesse os binários de serviço atualizados, o que é especialmente importante para cenários de depuração, como a depuração do código do cliente no código do serviço.

 Se o projeto de serviço for removido da solução, essa dependência de compilação explícita será invalidada. O Visual Studio não pode mais garantir que o projeto de serviço seja recriado conforme necessário.

 Para corrigir esse erro, você precisa recompilar manualmente o projeto de serviço:

1. No menu **Ferramentas**, clique em **Opções**.

2. Na caixa de diálogo **Opções** , expanda **projetos e soluções**e, em seguida, selecione **geral**.

3. Verifique se a caixa de seleção **Mostrar configurações avançadas de Build** está marcada e clique em **OK**.

4. Carregue o projeto de serviço WCF. Para obter mais informações, consulte [NIB como criar soluções de vários projetos](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).

5. Na caixa de diálogo **Configuration Manager** , defina a **configuração da solução ativa** como **depurar**. Para obter mais informações, consulte [Como criar e editar configurações](../ide/how-to-create-and-edit-configurations.md).

6. Em **Gerenciador de soluções**, selecione o projeto de serviço WCF.

7. No menu **Compilar** , clique em **Recompilar** para recriar o projeto de serviço WCF.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Data Services não são exibidos no navegador
 Quando ele tenta exibir uma representação XML de dados em um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], o Internet Explorer pode misinterpret os dados como um RSS feed. Você deve verificar se a opção para exibir RSS feeds está desabilitada.

 Para corrigir esse erro, desabilite os RSS feeds:

1. No Internet Explorer, no menu **Ferramentas**, clique em **Opções da Internet**.

2. Na guia **conteúdo** , na seção **feeds** , clique em **configurações**.

3. Na caixa de diálogo **configurações do feed** , desmarque a caixa de seleção **Ativar exibição de leitura do feed** e clique em **OK**.

4. Clique em **OK** para fechar a caixa de diálogo **Opções da Internet** .

## <a name="see-also"></a>Consulte também

- [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)