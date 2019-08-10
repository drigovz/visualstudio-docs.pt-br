---
title: Caixa de diálogo Configurar Referência de Serviço
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msvse_wcf.dlg.ConfigureServiceReference
helpviewer_keywords:
- WCF services, Configure Service Reference dialog box
- service references [Visual Studio], configuring behavior
- Configure Service Reference dialog box
ms.assetid: 25e4c36b-2db6-4e71-9010-b7068255d09d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1cf4a809c1353f2fe30383a312f65b6c623083db
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925679"
---
# <a name="configure-service-reference-dialog-box"></a>Caixa de diálogo Configurar Referência de Serviço

A caixa de diálogo **Configurar referência de serviço** permite que você configure o comportamento dos serviços Windows Communication Foundation (WCF).

Para acessar a caixa de diálogo **Configurar referência de serviço** , clique com o botão direito do mouse em uma referência de serviço em **Gerenciador de soluções** e escolha **Configurar referência de serviço**. Você também pode acessar a caixa de diálogo clicando no botão **avançado** na **caixa de diálogo Adicionar referência de serviço**.

## <a name="task-list"></a>Lista de tarefas

- Para alterar o endereço em que um serviço WCF está hospedado, insira o novo endereço no campo **endereço** .

- Para alterar o nível de acesso para classes em um cliente WCF, selecione uma palavra-chave de nível de acesso na lista **nível de acesso para classes geradas** .

- Para chamar os métodos de um serviço WCF de forma assíncrona, marque a caixa de seleção **gerar operações** assíncronas.

- Para gerar tipos de contrato de mensagem em um cliente WCF, marque a caixa de seleção **sempre gerar contratos de mensagem** .

- Para especificar os tipos de coleção de lista ou dicionário para um cliente WCF, selecione os tipos nas listas **tipo de coleção** e tipo de **coleção de dicionário** .

- Para desabilitar o compartilhamento de tipo, desmarque a caixa de seleção reutilizar os **tipos em assemblies referenciados** . Para habilitar o compartilhamento de tipo para um subconjunto de assemblies referenciados, marque a caixa de seleção reutilizar os **tipos em assemblies referenciados** , selecione reutilizar os **tipos em assemblies referenciados especificados**e selecione as referências desejadas na **referência lista de assemblies**.

## <a name="uielement-list"></a>Lista UIElement

**Endereço**

Atualiza o endereço Web em que uma referência de serviço procura um serviço. Por exemplo, durante o desenvolvimento, o serviço pode ser hospedado em um servidor de desenvolvimento e, posteriormente, movido para um servidor de produção, precisando de uma alteração de endereço.

> [!NOTE]
> O elemento address não estará disponível quando a caixa de diálogo **Configurar referência de serviço** for exibida na **caixa de diálogo Adicionar referência de serviço**.

**Nível de acesso para classes geradas**

Determina o nível de acesso do código para classes de cliente WCF.

> [!NOTE]
> Para projetos de site, essa opção é sempre definida `Public` como e não pode ser alterada. Para obter mais informações, consulte [Solucionando problemas de referências de serviço](../data-tools/troubleshooting-service-references.md).

**Gerar operações assíncronas**

Determina se os métodos de serviço WCF são chamados de forma síncrona (o padrão) ou assincronamente.

**Gerar operações baseadas em tarefas**

Ao escrever código assíncrono, essa opção permite que você aproveite a TPL (biblioteca paralela de tarefas) que foi introduzida com o .NET 4. Consulte a [TPL (biblioteca de paralelo de tarefas)](/dotnet/standard/parallel-programming/task-parallel-library-tpl).

**Sempre gerar contratos de mensagem**

Determina se os tipos de contrato de mensagem são gerados para um cliente WCF. Para obter mais informações sobre os contratos de mensagem, consulte [usando contratos de mensagem](/dotnet/framework/wcf/feature-details/using-message-contracts).

**Tipo de coleção**

Especifica o tipo de coleção de lista para um cliente WCF. O tipo padrão é <xref:System.Array>.

**Tipo de coleção de dicionário**

Especifica o tipo de coleção de dicionário para um cliente WCF. O tipo padrão é <xref:System.Collections.Generic.Dictionary%602>.

**Usar novamente os tipos em assemblies consultados**

Determina se um cliente WCF tenta reutilizar o que já existe em assemblies referenciados em vez de gerar novos tipos quando um serviço é adicionado ou atualizado. Por padrão, essa opção está marcada.

**Usar novamente os tipos em todos os assemblies consultados**

Quando selecionado, todos os tipos na **lista assemblies referenciados** são reutilizados, se possível. Por padrão, essa opção é selecionada.

**Usar novamente os tipos em determinados assemblies consultados**

Quando selecionado, somente os tipos selecionados na **lista assemblies referenciados** são reutilizados.

**Lista de assemblies referenciados**

Contém uma lista de assemblies referenciados para o projeto ou site. Quando você seleciona **reutilizar os tipos em assemblies referenciados especificados**, você pode selecionar ou limpar assemblies individuais.

**Adicionar Referência Web**

Exibe a caixa de diálogo **Adicionar referência Web** .

> [!NOTE]
> Essa opção só deve ser usada para projetos direcionados à versão 2,0 do .NET Framework.
>
> [!NOTE]
> O botão **Adicionar referência Web** só estará disponível quando a caixa de diálogo **Configurar referência de serviço** for exibida na **caixa de diálogo Adicionar referência de serviço**.

## <a name="see-also"></a>Consulte também

- [Como: Adicionar uma referência a um serviço Web](how-to-add-update-or-remove-a-wcf-data-service-reference.md)
- [Serviços do Windows Communication Foundation e WCF Data Services](../data-tools/configure-service-reference-dialog-box.md)