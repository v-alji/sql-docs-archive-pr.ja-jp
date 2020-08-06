---
title: SQL Server コンポーネント |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Upgrade Advisor, components
- listing components to analyze
- Upgrade Advisor [SQL Server], components
- component analysis [Upgrade Advisor]
- finding components to analyze
- locating components to analyze
- detecting components to analyze
- server names [Upgrade Advisor]
- analyzing system [Upgrade Advisor], component list
- identifying components to analyze
ms.assetid: 539b9525-ce3f-4950-9146-5527a5a297ee
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 95fe39ce8e616b238cf7c70763e7cf1819341f16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742781"
---
# <a name="sql-server-components"></a><span data-ttu-id="753e4-102">SQL Server のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="753e4-102">SQL Server Components</span></span>
  <span data-ttu-id="753e4-103">アップグレードアドバイザー分析ウィザードは、、、 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 、またはがインストールされているローカルコンピューターまたはリモートコンピューターに対して実行でき [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="753e4-103">You can run the Upgrade Advisor Analysis Wizard against a local or remote computer that has [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] installed.</span></span> <span data-ttu-id="753e4-104">アップグレード前の分析における最初の手順は、分析対象のコンピューターとコンポーネントを特定することです。</span><span class="sxs-lookup"><span data-stu-id="753e4-104">The first step in the pre-upgrade analysis is to identify the computer and components for analysis.</span></span>  
  
## <a name="options"></a><span data-ttu-id="753e4-105">Options</span><span class="sxs-lookup"><span data-stu-id="753e4-105">Options</span></span>  
 <span data-ttu-id="753e4-106">**コンピューター名**</span><span class="sxs-lookup"><span data-stu-id="753e4-106">**Computer name**</span></span>  
 <span data-ttu-id="753e4-107">分析するコンピューターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="753e4-107">Specifies the name of the computer to analyze.</span></span> <span data-ttu-id="753e4-108">アップグレードアドバイザーによって、[**サーバー名**] ボックスにローカルコンピューター名が入力されます。</span><span class="sxs-lookup"><span data-stu-id="753e4-108">Upgrade Advisor populates the **Server name** box with the local computer name.</span></span> <span data-ttu-id="753e4-109">ローカル コンピューターに接続する場合は、"." および "localhost" も使用できます。</span><span class="sxs-lookup"><span data-stu-id="753e4-109">You can also use "." and "localhost" to connect to the local computer.</span></span>  
  
 <span data-ttu-id="753e4-110">別のコンピューターを分析するには、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="753e4-110">To analyze a different computer, use the following guidelines:</span></span>  
  
-   <span data-ttu-id="753e4-111">クラスター化されていないインスタンスをスキャンするには、コンピューター名を入力します。</span><span class="sxs-lookup"><span data-stu-id="753e4-111">To scan nonclustered instances, enter the computer name.</span></span>  
  
-   <span data-ttu-id="753e4-112">クラスター化されたインスタンスをスキャンするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンスの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="753e4-112">To scan clustered instances, enter the name of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster instance.</span></span>  
  
-   <span data-ttu-id="753e4-113">クラスターのノードにインストールされている非クラスター化コンポーネントをスキャンするには、フェールオーバークラスターノードのコンピューター名を入力します。</span><span class="sxs-lookup"><span data-stu-id="753e4-113">To scan nonclustered components that are installed on a node of a cluster, enter the computer name of the failover cluster node.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="753e4-114">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス名は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="753e4-114">Do not include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance name.</span></span>  
  
 <span data-ttu-id="753e4-115">コンピューター名を指定する代わりに、IP アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="753e4-115">Instead of specifying the computer name, you can specify the IP address.</span></span>  
  
 <span data-ttu-id="753e4-116">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] をスキャンする場合、ローカル サーバーの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="753e4-116">If scanning [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], you must specify the name of the local computer.</span></span> <span data-ttu-id="753e4-117">アップグレード アドバイザーでは、ローカル レポート サーバーだけがスキャンされます。</span><span class="sxs-lookup"><span data-stu-id="753e4-117">Upgrade Advisor scans local report servers only.</span></span>  
  
 <span data-ttu-id="753e4-118">**Detect**</span><span class="sxs-lookup"><span data-stu-id="753e4-118">**Detect**</span></span>  
 <span data-ttu-id="753e4-119">[**検出**] ボタンは、指定されたコンピューターにアクセスし、分析するコンポーネントを検出します。</span><span class="sxs-lookup"><span data-stu-id="753e4-119">The **Detect** button accesses the specified computer and detects components to analyze:</span></span>  
  
-   <span data-ttu-id="753e4-120">リモート コンピューター上の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを分析する場合は、リモート コンピューター上でリモート レジストリ サービスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="753e4-120">If you are analyzing a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance on a remote computer, you must enable the remote registry services on the remote computer.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="753e4-121">は、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、または [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のインスタンスがコンピューターのレジストリで見つかった場合に検出されます。</span><span class="sxs-lookup"><span data-stu-id="753e4-121">is detected if an instance of [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], or [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] is found in the computer's registry.</span></span>  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="753e4-122">は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスがコンピューターのレジストリで見つかった場合に検出されます。</span><span class="sxs-lookup"><span data-stu-id="753e4-122">is detected if an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is found in the computer's registry.</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="753e4-123">は、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] がコンピューターのレジストリで見つかった場合に検出されます。</span><span class="sxs-lookup"><span data-stu-id="753e4-123">is detected if [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is found in the computer's registry.</span></span> <span data-ttu-id="753e4-124">ただし、アップグレード アドバイザーでは、ローカル レポート サーバーだけがスキャンされます。</span><span class="sxs-lookup"><span data-stu-id="753e4-124">However, Upgrade Advisor scans local report servers only.</span></span>  
  
 <span data-ttu-id="753e4-125">**コンポーネント**</span><span class="sxs-lookup"><span data-stu-id="753e4-125">**Components**</span></span>  
 <span data-ttu-id="753e4-126">分析するコンポーネントを選択します。</span><span class="sxs-lookup"><span data-stu-id="753e4-126">Select the components to analyze.</span></span> <span data-ttu-id="753e4-127">[**検出**] ボタンをクリックすると、コンピューターにインストールされているすべてのコンポーネントを選択できます。</span><span class="sxs-lookup"><span data-stu-id="753e4-127">You can click the **Detect** button to select all the components installed on the computer.</span></span> <span data-ttu-id="753e4-128">このコンピューターにインストールされていることが検出されたコンポーネントの横に、チェック マークが表示されます。</span><span class="sxs-lookup"><span data-stu-id="753e4-128">A check mark will appear next to the components that are detected as installed on the computer.</span></span> <span data-ttu-id="753e4-129">各コンポーネントの横にあるチェック ボックスをオンまたはオフにして、分析するコンポーネントを手動で選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="753e4-129">You can also manually select the components to analyze by selecting or clearing the check box next to each component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="753e4-130">参照</span><span class="sxs-lookup"><span data-stu-id="753e4-130">See Also</span></span>  
 <span data-ttu-id="753e4-131">[アップグレードアドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="753e4-131">[Working with Upgrade Advisor](../../../2014/sql-server/install/working-with-upgrade-advisor.md) </span></span>  
 [<span data-ttu-id="753e4-132">アップグレード アドバイザーのユーザー インターフェイス リファレンス</span><span class="sxs-lookup"><span data-stu-id="753e4-132">Upgrade Advisor User Interface Reference</span></span>](../../../2014/sql-server/install/upgrade-advisor-user-interface-reference.md)  
  
  
