---
title: Criando aplicativos ClickOnce para outros a serem implantados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3307fc124f50e8c9f73749293c36f53be36c5e3c
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252457"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Criar aplicativos ClickOnce para que outros usuários implantem
Nem todos os desenvolvedores que estão criando implantações do ClickOnce planejam implantar os próprios aplicativos. Muitos deles apenas empacotam seu aplicativo usando o ClickOnce e, em seguida, entregam os arquivos para um cliente, como uma grande corporação. O cliente se torna aquele responsável por hospedar o aplicativo em sua rede. Este tópico discute alguns dos problemas inerentes a tais implantações em versões do .NET Framework antes da versão 3,5. Em seguida, ele descreve uma nova solução fornecida usando o novo recurso "usar manifesto para confiança" no .NET Framework 3,5. Por fim, ele conclui as estratégias recomendadas para a criação de implantações do ClickOnce para clientes que ainda estão usando versões mais antigas do .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemas envolvidos na criação de implantações para clientes
 Vários problemas ocorrem quando você planeja fornecer uma implantação para um cliente. O primeiro problema diz respeito à assinatura de código. Para ser implantado em uma rede, o manifesto de implantação e o manifesto do aplicativo de uma implantação do ClickOnce devem ser assinados com um certificado digital. Isso gera a pergunta de se deve ser usado o certificado do desenvolvedor ou o certificado do cliente ao assinar os manifestos.

 A questão de qual certificado usar é essencial, uma vez que a identidade de um aplicativo ClickOnce se baseia na assinatura digital do manifesto de implantação. Se o desenvolvedor assinar o manifesto de implantação, poderá levar a conflitos se o cliente for uma empresa de grande porte e mais de uma divisão da empresa implantar uma versão personalizada do aplicativo.

 Por exemplo, digamos que a Adventure Works tem um departamento financeiro e um departamento de recursos humanos. Ambos os departamentos licenciam um aplicativo ClickOnce da Microsoft Corporation que gera relatórios de dados armazenados em um banco de dado SQL. A Microsoft fornece a cada departamento uma versão do aplicativo que é personalizada para seus dados. Se os aplicativos forem assinados com o mesmo certificado Authenticode, um usuário que tentar usar ambos os aplicativos encontraria um erro, pois o ClickOnce consideraria o segundo aplicativo como sendo idêntico ao primeiro. Nesse caso, o cliente pode experimentar efeitos colaterais imprevisíveis e indesejados que incluem a perda de quaisquer dados armazenados localmente pelo aplicativo.

 Um problema adicional relacionado à assinatura de código é `deploymentProvider` o elemento no manifesto de implantação, que informa ao ClickOnce onde procurar atualizações de aplicativo. Esse elemento deve ser adicionado ao manifesto de implantação antes de assiná-lo. Se esse elemento for adicionado posteriormente, o manifesto de implantação deverá ser assinado novamente.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Exigir que o cliente assine o manifesto de implantação
 Uma solução para esse problema de implantações não exclusivas é fazer com que o desenvolvedor assine o manifesto do aplicativo e o cliente assine o manifesto de implantação. Embora essa abordagem funcione, ela apresenta outros problemas. Como um certificado Authenticode deve permanecer como um ativo protegido, o cliente não pode apenas fornecer o certificado ao desenvolvedor para assinar a implantação. Embora o cliente possa assinar o próprio manifesto de implantação usando as ferramentas gratuitas disponíveis com o SDK do .NET Framework, isso pode exigir mais conhecimento técnico do que o cliente está disposto ou capaz de fornecer. Nesses casos, o desenvolvedor geralmente cria um aplicativo, um site ou outro mecanismo por meio do qual o cliente pode enviar sua versão do aplicativo para assinatura.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>O impacto da assinatura de cliente na segurança do aplicativo ClickOnce
 Mesmo que o desenvolvedor e o cliente concordem que o cliente deve assinar o manifesto do aplicativo, isso gera outros problemas que envolvem a identidade do aplicativo, especialmente à medida que se aplica à implantação de aplicativos confiáveis. (Para obter mais informações sobre esse recurso, consulte [visão geral da implantação de aplicativo confiável](../deployment/trusted-application-deployment-overview.md).) Digamos que a Adventure Works queira configurar seus computadores cliente para que qualquer aplicativo fornecido a ele pela Microsoft Corporation seja executado com confiança total. Se a Adventure Works assinar o manifesto de implantação, o ClickOnce usará a assinatura de segurança da Adventure Works para determinar o nível de confiança do aplicativo.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Criar implantações de clientes usando o manifesto do aplicativo para confiança
 O ClickOnce no .NET Framework 3,5 contém um novo recurso que oferece aos desenvolvedores e clientes uma nova solução para o cenário de como os manifestos devem ser assinados. O manifesto do aplicativo ClickOnce dá suporte a um `<useManifestForTrust>` novo elemento chamado que permite a um desenvolvedor significar que a assinatura digital do manifesto do aplicativo é o que deve ser usado para tomar decisões de confiança. O desenvolvedor usa as ferramentas de empacotamento do ClickOnce, como o *Mage. exe*, o *MageUI. exe*e o Visual Studio, para incluir esse elemento no manifesto do aplicativo, bem como inserir o nome do editor e o nome do aplicativo no manifesto.

 Ao usar `<useManifestForTrust>`o, o manifesto de implantação não precisa ser assinado com um certificado Authenticode emitido por uma autoridade de certificação. Em vez disso, ele pode ser assinado com o que é conhecido como um certificado autoassinado. Um certificado autoassinado é gerado pelo cliente ou pelo desenvolvedor usando ferramentas SDK de .NET Framework padrão e, em seguida, aplicado ao manifesto de implantação usando as ferramentas de implantação padrão do ClickOnce. Para obter mais informações, consulte [MakeCert](/windows/desktop/SecCrypto/makecert).

 O uso de um certificado autoassinado para o manifesto de implantação apresenta várias vantagens. Ao eliminar a necessidade de o cliente obter ou criar seu próprio certificado Authenticode, `<useManifestForTrust>` o simplifica a implantação para o cliente, ao mesmo tempo que permite que o desenvolvedor mantenha sua própria identidade visual no aplicativo. O resultado é um conjunto de implantações assinadas que são mais seguras e têm identidades de aplicativo exclusivas. Isso elimina o possível conflito que pode ocorrer na implantação do mesmo aplicativo em vários clientes.

 Para obter informações passo a passo sobre como criar uma implantação do ClickOnce com `<useManifestForTrust>` habilitado, consulte [passo a passos: Implante manualmente um aplicativo ClickOnce que não requer nova assinatura e que preserva informações](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)de identidade visual.

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Como o manifesto do aplicativo para confiança funciona em tempo de execução
 Para entender melhor como usar o manifesto do aplicativo para confiança funciona em tempo de execução, considere o exemplo a seguir. Um aplicativo ClickOnce direcionado para o .NET Framework 3,5 é criado pela Microsoft. O manifesto do aplicativo usa `<useManifestForTrust>` o elemento e é assinado pela Microsoft. A Adventure Works assina o manifesto de implantação usando um certificado autoassinado. Os clientes da Adventure Works são configurados para confiar em qualquer aplicativo assinado pela Microsoft.

 Quando um usuário clica em um link para o manifesto de implantação, o ClickOnce instala o aplicativo no computador do usuário. As informações de certificado e de implantação identificam o aplicativo exclusivamente para o ClickOnce no computador cliente. Se o usuário tentar instalar o mesmo aplicativo novamente de um local diferente, o ClickOnce poderá usar essa identidade para determinar se o aplicativo já existe no cliente.

 Em seguida, o ClickOnce examina o certificado Authenticode que é usado para assinar o manifesto do aplicativo, que determina o nível de confiança que o ClickOnce concederá. Como a Adventure Works configurou seus clientes para confiar em qualquer aplicativo assinado pela Microsoft, esse aplicativo ClickOnce recebe confiança total. Para obter mais informações, consulte [visão geral da implantação de aplicativo confiável](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Criar implantações de clientes para versões anteriores
 E se um desenvolvedor estiver implantando aplicativos ClickOnce para clientes que estão usando versões mais antigas do .NET Framework? As seções a seguir resumem várias soluções recomendadas, junto com os benefícios e as desvantagens de cada uma.

### <a name="sign-deployments-on-behalf-of-customer"></a>Assinar implantações em nome do cliente
 Uma estratégia de implantação possível é que o desenvolvedor crie um mecanismo para assinar implantações em nome de seus clientes, usando a chave privada do próprio cliente. Isso impede que o desenvolvedor precise gerenciar chaves privadas ou vários pacotes de implantação. O desenvolvedor apenas fornece a mesma implantação para cada cliente. Cabe ao cliente personalizá-lo para seu ambiente usando o serviço de assinatura.

 Uma desvantagem desse método é o tempo e as despesas necessárias para implementá-lo. Embora tal serviço possa ser criado usando as ferramentas fornecidas no SDK do .NET Framework, ele adicionará mais tempo de desenvolvimento ao ciclo de vida do produto.

 Conforme observado anteriormente neste tópico, outra desvantagem é que a versão de cada cliente do aplicativo terá a mesma identidade de aplicativo, o que pode levar a conflitos. Se essa for uma preocupação, o desenvolvedor poderá alterar o campo de nome usado ao gerar o manifesto de implantação para dar um nome exclusivo a cada aplicativo. Isso criará uma identidade separada para cada versão do aplicativo e eliminará possíveis conflitos de identidade. Esse campo corresponde ao `-Name` argumento para Mage. exe e ao campo **nome** na guia **nome** em MageUI. exe.

 Por exemplo, digamos que o desenvolvedor tenha criado um aplicativo chamado Application1. Em vez de criar uma única implantação com o campo Name definido como Application1, o desenvolvedor pode criar várias implantações com uma variação específica do cliente sobre esse nome, como Application1-CustomerA, Application1-Clienteb e assim por diante.

### <a name="deploy-using-a-setup-package"></a>Implantar usando um pacote de instalação
 Uma segunda estratégia de implantação possível é gerar um projeto de instalação da Microsoft para executar a implantação inicial do aplicativo ClickOnce. Isso pode ser fornecido em um dos vários formatos diferentes: como uma implantação MSI, como um executável de instalação (. EXE) ou como um arquivo de gabinete (. cab) junto com um script em lotes.

 Usando essa técnica, o desenvolvedor forneceria ao cliente uma implantação que inclui os arquivos de aplicativo, o manifesto do aplicativo e um manifesto de implantação que serve como modelo. O cliente executaria o programa de instalação, que os solicitaria por uma URL de implantação (o local do servidor ou do compartilhamento de arquivos do qual os usuários instalarão o aplicativo ClickOnce), bem como um certificado digital. O aplicativo de instalação também pode optar por solicitar opções de configuração adicionais do ClickOnce, como intervalo de verificação de atualização. Depois que essas informações forem coletadas, o programa de instalação gerará o manifesto de implantação real, o assinará e publicaria o aplicativo ClickOnce no local do servidor designado.

 Há três maneiras pelas quais o cliente pode assinar o manifesto de implantação nesta situação:

1. O cliente pode usar um certificado válido emitido por uma autoridade de certificação (CA).

2. Como uma variação nessa abordagem, o cliente pode optar por assinar seu manifesto de implantação com um certificado autoassinado. A desvantagem disso é que isso fará com que o aplicativo exiba as palavras "Editor desconhecido" quando o usuário for perguntado se deseja instalá-lo. No entanto, o benefício é que ele impede que clientes menores tenham que gastar tempo e dinheiro necessários para um certificado emitido por uma autoridade de certificação.

3. Por fim, o desenvolvedor pode incluir seu próprio certificado autoassinado no pacote de instalação. Isso apresenta os possíveis problemas com a identidade do aplicativo discutida anteriormente neste tópico.

   A desvantagem do método de projeto de implantação da instalação é o tempo e as despesas necessárias para criar um aplicativo de implantação personalizado.

### <a name="have-customer-generate-deployment-manifest"></a>Fazer com que o cliente gere o manifesto de implantação
 Uma terceira estratégia de implantação possível é distribuir apenas os arquivos de aplicativo e o manifesto do aplicativo para o cliente. Nesse cenário, o cliente é responsável por usar o SDK do .NET Framework para gerar e assinar o manifesto de implantação.

 A desvantagem desse método é que ele exige que o cliente instale as ferramentas SDK do .NET Framework e tenha um desenvolvedor ou administrador do sistema que seja capacitado para usá-las. Alguns clientes podem solicitar uma solução que exija pouco ou nenhum esforço técnico em sua parte.

## <a name="see-also"></a>Consulte também
- [Implantar aplicativos ClickOnce para servidores de teste e produção sem assinatura](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Passo a passo: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Passo a passo: Como implantar manualmente um aplicativo ClickOnce que não requer nova assinatura e que preserva informações de identidade visual](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)