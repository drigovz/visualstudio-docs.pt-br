---
title: Usar chaves do produto (Product Keys) para dar suporte a demonstrações da Internet por meio dos Serviços de Terminal | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/19/2019
ms.topic: conceptual
description: Saiba como usar as chaves do produto (Product Keys) para dar suporte a demonstrações da Internet por meio dos Serviços de Terminal e habilitar o acesso ao RDS
ms.openlocfilehash: 19faa64b7eeaebc1b92ca965f686795b31e00e7e
ms.sourcegitcommit: 9fc8b144d4ed1c46aba87c0b7e1d24454e0eea9d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68493377"
---
# <a name="internet-demonstrations-via-terminal-services"></a>Demonstrações da Internet por meio dos Serviços de Terminal
Com uma assinatura do Visual Studio, você pode fornecer aos usuários finais acesso a demonstrações de seus programas na Internet via Serviços de Terminal (Windows Server 2003 ou Windows Server 2008) ou Serviços de Área de Trabalho Remota (Windows Server 2008 R2 e posterior). Dessa forma, até 200 usuários anônimos poderão acessar simultaneamente a demonstração. A demonstração não deverá usar dados de produção. Os assinantes do Visual Studio são licenciados para demonstrar aplicativos aos usuários finais. Essa demonstração de Internet usando o TS (Serviços de Terminal) ou o RDS (Serviços de Área de Trabalho Remota) é o único cenário em que os usuários finais sem uma assinatura do Visual Studio podem interagir com o aplicativo de demonstração enquanto o software é licenciado por meio das assinaturas do Visual Studio.

Trata-se de uma adição aos direitos de Desenvolvimento/Teste, em que os assinantes do Visual Studio podem usar tantas conexões ao TS ou ao RDS que forem necessárias.

## <a name="enabling-rds-access"></a>Habilitando o acesso ao RDS
Os assinantes do Visual Studio podem aumentar o número de usuários com acesso ao Windows Server por meio do RDS. Para isso, basta inserir a chave do produto (Product Key) fornecida na guia [Chaves do Produto (Product Keys)](https://my.visualstudio.com/productkeys?wt.mc_id=o~msft~docs) no [portal do assinante](https://my.visualstudio.com?wt.mc_id=o~msft~docs). Para obter a chave do produto (Product Key), conecte-se à página Chaves do Produto (Product Keys) e role para baixo até a versão do Windows Server que você está executando. Localize “Conexões de <usuário ou dispositivo> dos Serviços de Área de Trabalho Remota do Windows Server <versão> R2” e clique no link **Solicitar Chave**. Se, por exemplo, você estiver usando o RDS no Windows Server 2012 R2 e sua implantação usar CALs de usuário, escolha “Conexões de usuário dos Serviços de Área de Trabalho Remota do Windows Server 2012 (50)”.
Cinco chaves de cada tipo estão disponíveis para o Windows Server 2008 R2, sendo que cada chave comporta 20 conexões. Quatro chaves de cada tipo são fornecidas para o Windows Server 2012 R2, sendo que cada uma comporta 50 conexões.

## <a name="to-enable-additional-connections-in-windows-server"></a>Para habilitar as conexões adicionais no Windows Server:
1. Abra o Gerenciador de Servidores.
2. Abra a lista de Servidores no painel de navegação à esquerda.
3. Clique com o botão direito do mouse no servidor de licença e escolha “Instalar Licenças”.
4. Siga as etapas no assistente.  Ao selecionar o tipo de contrato, escolha “Pacote de Licença (comercial)” e insira a chave do produto (Product Key) obtida no portal do usuário.

Se as seguintes condições forem atendidas, os usuários finais poderão conectar-se para acessar os aplicativos pelo RDS:
- Os usuários devem ser anônimos (em estado não autenticado).
- As conexões devem ser feitas pela Internet.
- Até 200 conexões de usuário podem ser usadas ao mesmo tempo para demonstrações do aplicativo.
- As chaves do produto (Product Keys) para habilitar as conexões de usuário devem ser obtidas por um assinante do Visual Studio.

## <a name="next-steps"></a>Próximas etapas
Se precisar de diretrizes para implantar o RDS, confira a série de blogs em várias partes na **implantação da sessão do RDS (Serviços de Área de Trabalho Remota) 2012** em https://techcommunity.microsoft.com/t5/Ask-The-Performance-Team/bg-p/AskPerf. 

Se tiver dúvidas, acesse o [fórum dos Serviços de Área de Trabalho Remota da Microsoft](https://social.technet.microsoft.com/Forums/windowsserver/home?forum=winserverTS).
