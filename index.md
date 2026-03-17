---
layout: page
title: Fortress64 - Securing Your Digital Privacy
menubar: menu
---
# We are done asking permission to use our own devices

*A legal and technical case against bootloader locking — and a call to act*

---

## TL;DR

Samsung is using EU law as an excuse to permanently lock the software on devices you own. They claim the law requires it. It does not. The law only says devices must *ship* locked — not that you can never unlock them. This misrepresentation has serious consequences: it kills independent repair, accelerates electronic waste, enables mass data collection you cannot audit, and creates an artificial monopoly over fixing software on hardware you paid for. The legal tools to fight this exist. This article explains them — and asks you to help use them.

> *I am not a legal specialist. I am a white hat hacker, computer hardware engineer, and developer with decades of experience who knows when something is technically wrong and legally suspicious. I want to connect with legal warriors to discuss the best approach together. If that is you — or if you simply want to vote for this cause through a European Citizens' Initiative — read on.*

---

## A personal note before we begin

I have been a Linux and Android developer since the early days. Long before that — back in the 90s, as a teenager — I was hacking into school systems and company servers. Almost nobody knows my work. I am a ghost — invisible, but always present, like the pillar dependency in that famous [XKCD comic](https://xkcd.com/2347/): a critical piece of infrastructure that everyone relies on and nobody thinks about. That is fine. I do not like the spotlight, and I have no interest in having my ass kissed.

If you have been in the Linux and Android scene since the beginning, I am fairly sure my code is powering almost every device in your house, or running on some device somewhere near you. Yes, rebels are born — and crafted. I respect my privacy and will keep my identity to myself.

I have never liked anything served to me that I cannot check or control. The idea of not being able to run my own software — or software I trust — on my own devices is suffocating. I know manufacturers are monitoring us around the clock. I know they try to hide their security issues. What if we had another SSH xz backdoor, another Stagefright (2015), another QuadRooter (2016) — sitting unpatched on a locked device where neither the user nor independent researchers can do anything about it? That thought should concern everyone.

Here on XDA Forums, opinions are divided. Some users have simply accepted manufacturer restrictions as inevitable, treating the situation as a lost cause. Others have gone further, repeating manufacturer talking points as fact without questioning them. And others are actively cracking the "security" measures manufacturers impose, proving that these locks serve control rather than protection.

We should not be dominated by those who accept what they are served because it feels "fine" to them, or because they do not mind being tracked around the clock. One person's indifference to privacy does not stop where another person's privacy begins. Your comfort with surveillance does not give manufacturers the right to impose it on everyone. Privacy is not a setting you choose for yourself — it is a right that protects all of us, whether we exercise it or not.

---

## The Radio Equipment Directive is being misused

Samsung's decision to remove bootloader unlocking in One UI 8 is the clearest recent example of a broader pattern: manufacturers using EU regulations as an excuse to lock down hardware they have already sold to you.

The regulation most often cited is the Radio Equipment Directive, expanded in 2022 by Delegated Act 2022/30/EU. Since August 2025, this requires devices to meet three cybersecurity standards: they must not interfere with networks, they must protect personal data, and devices used for financial transactions must include anti-fraud protections.

That is genuinely all it says. It sets goals — "the device must be secure" — but it does not specify how manufacturers must achieve those goals. Think of it like a building regulation that says "this building must be fire safe." It does not tell the architect to use one specific type of door — and a fire door must be openable when there is a fire, so the firefighters can come in and douse the flames. A vault door, by contrast, is designed so that only the owner can open it. What manufacturers are doing is installing a vault door on your property, keeping the combination for themselves — on something they no longer own and have already been paid for — so they would rather leave you burning inside.

**Locking the bootloader permanently is a choice, not a legal obligation.** It is also a very convenient one: a locked bootloader hides proprietary software from scrutiny, obscures bugs from independent researchers, and makes it far harder for anyone outside the company to see what is actually running on your device — or what data it is sending out. Beyond that, it is a form of vendor lock-in: once your device is locked to the manufacturer's ecosystem, switching becomes painful, expensive, or simply impossible — which is precisely the point. The law sets outcomes, not methods — and permanent bootloader locking is a manufacturer choice dressed up as a legal obligation.

The directive does not say that users cannot unlock their own devices. What it requires is only that devices *ship* with the bootloader locked — not that users are permanently prevented from unlocking them afterwards. These are two very different things. A simple, accessible unlock process for the owner is entirely compatible with the law. Manufacturers are deliberately blurring this distinction.

Their argument also fails on four specific points:

### 1. The cellular modem handles radio compliance, not the OS

Protecting network frequencies is the job of the cellular modem, not the operating system. Fairphone confirms this directly: custom ROMs do not modify the isolated radio and modem behaviour and therefore do not violate the directive. Fairphone continues to provide the necessary software components to community ROM projects as a result, proving that compliance and user freedom are not in conflict.

### 2. A custom ROM can be just as secure as a stock one — and often more so

The cybersecurity requirements say a device must be secure — they do not say the manufacturer must be the only one allowed to provide the software. GrapheneOS is widely regarded as significantly more secure than stock Android, precisely because its code is open to scrutiny, vulnerabilities are found faster, and there is no commercial incentive to delay patches.

### 3. Laptops face the exact same laws — and mostly nobody locks them

Windows laptops are covered by the same EU cybersecurity and radio equipment regulations, yet no manufacturer locks the bootloader to prevent users from reinstalling the OS or switching to Linux. Intel-based Macs are the same — fully open to alternative operating systems, well supported by the Linux community. Interestingly, Apple's newer Silicon Macs are starting to move in the other direction: Apple does not officially support alternative operating systems on M-series hardware and has implemented Secure Boot that makes booting non-Apple-signed software difficult. The community project Asahi Linux exists specifically to reverse engineer Apple's entirely undocumented platform just to make Linux possible. Sound familiar? The smartphone pattern is spreading to desktops — and it starts with the same argument: security. Meanwhile Microsoft has faced similar criticism for Windows 11's artificially strict hardware requirements, locking out perfectly capable machines not for genuine security reasons but to push users toward new hardware — a textbook example of planned obsolescence dressed up as a safety feature, and one that belongs in the same conversation as bootloader locking.

### 4. The directive protects the network, not the manufacturer's business model

Articles 3(3)(d), (e), and (f) address network security, data privacy, and fraud protection — not OS modifications. The law exists to protect people from harmful devices, not to give manufacturers permanent control over products they have already sold.

---

### On eSIM

Some manufacturers claim bootloader unlocking could compromise eSIM security. This is technically false. eSIM profiles are stored in a completely separate, isolated secure element — a dedicated chip the operating system cannot directly access. These profiles survive bootloader unlocking and factory resets entirely intact. Manufacturers who make this argument either know it is wrong, or should.

---

### On absolute security

As any security professional will tell you, claiming absolute security is snake oil. You can build a safe door thirty centimetres thick — but that does not make it thief-proof, practical, affordable, standards-compliant, or easy to update when a vulnerability is discovered. We have personally identified firmware bugs in Xiaomi devices that caused batteries to very slightly overcharge — above the battery's rated maximum voltage — over time, eventually causing them to swell, fail, and turn into a pocket bomb. This is direct proof that manufacturer software is never free of errors.

We also do not see any warnings when connecting to a WPA or WPA2 network, despite WPA2 being vulnerable to deauthentication attacks and WPA to outright cracking. And in Europe in 2026, you can still set your router region to Japan and use channel 14 on your Wi-Fi — a channel illegal in most of the world. You can still buy 1000mW (1 Watt) Wi-Fi devices online without any restriction. Why so serious about security? 🃏

If manufacturers truly wanted to protect you, they would have addressed these issues years ago — or at the very least warned you when you connect to an older, insecure Wi-Fi repeater. They have not. Manufacturer software is not the gold standard it is presented as.

Our own EDL recovery tool live USB image makes this even clearer: it can bypass manufacturer EDL authentication entirely on certain devices. We built it for legitimate repair — but a determined attacker with the right knowledge could do the same. No lock is unbreakable. The question is not whether a device is perfectly secure, but whether the restrictions on the *owner* actually improve security in practice — or merely create the illusion of it while serving the manufacturer's interests.

---

## What manufacturers and Google actually gain from locking you out

It is worth being direct about why locking benefits manufacturers — because it has nothing to do with your security and everything to do with their business model.

A locked device means you are permanently dependent on the manufacturer's ecosystem. You use their app store, their services, their advertising platform. You cannot remove their bloatware. You cannot audit what data is being sent, to whom, or how often. Every locked device is a captive audience — for targeted advertising, for data harvesting, for paid services you cannot replace with alternatives. Unlocking breaks that dependency, and that is precisely why they do not want you to do it.

Google's interests are aligned with this. Google Play is the dominant app distribution channel on Android, generating enormous revenue through its 15–30% cut of every purchase and subscription. F-Droid and AuroraStore threaten that monopoly by offering software distribution that bypasses Google entirely. A locked ecosystem funnels every user back to Google Play — and keeps them there. This is not incidental — it is the business model.

Locking also dramatically reduces warranty and support costs. A bricked device that cannot be recovered by the user becomes a repair or replacement job — billable to the consumer. A device that could be fixed in minutes with the right tools instead generates a service appointment, a mainboard replacement, and a bill for something trivially simple.

Finally, locked devices accelerate the replacement cycle. A phone that cannot run community software after manufacturer support ends becomes e-waste sooner. That means another sale. The sustainability cost is borne by the environment and the consumer — the profit goes to the manufacturer.

---

## "Warranty void" — another legal bluff

When you unlock a bootloader or flash a custom ROM, most manufacturers immediately tell you your warranty is void. This is presented as fact. It is, largely, a bluff — and in the EU it is often not even legally accurate.

Under EU law, simply modifying or changing the software of your device is not sufficient reason to void your statutory warranty. The seller must prove that the specific defect you are claiming was actually caused by your custom ROM software — not merely that you modified the software at some point. The burden of proof sits with the manufacturer, not with you.

There are two separate types of warranty in the EU:

- The **statutory warranty** is compulsory by law — it cannot be waived, voided, or signed away, and it covers you for at least two years from purchase.
- The **voluntary warranty** is an additional commercial guarantee that the manufacturer offers on top, and this is the part they can choose to limit or void.

Most manufacturers deliberately blur this distinction, telling consumers their "warranty is void" without specifying which one — leading people to believe they have lost all protection when in reality only the optional commercial extension may be affected.

If a seller refuses to honour your statutory warranty, they must prove you caused the problem. They cannot simply point to the fact that you flashed a custom ROM and call it done. A cracked screen, a failed cellular antenna, a charging port that stops working — none of these are plausibly caused by custom software, and a manufacturer who refuses warranty service on that basis is on very weak legal ground.

### The hardware engineering argument

Manufacturers claim that custom software could damage hardware — pushing components beyond safe limits — and therefore voiding the warranty makes sense as a protective measure. This argument sounds plausible to most users. To a hardware engineer, it is a farce.

For example: every modern device contains a PMU — a Power Management Unit — a dedicated hardware component whose job is to manage and enforce safe power limits independently of whatever software is running. Battery charging voltage and cutoff thresholds, Wi-Fi transmit power, the power delivered to connected OTG devices — these are governed at the hardware level by the PMU and its associated protection circuits. Similarly, CPUs are governed by their own dedicated throttling and thermal management circuits with hardware-enforced temperature limits. The firmware communicates requests to these systems — but the hardware enforces its own hard limits regardless of what the software asks for.

The principle is simple: **a device must be able to protect itself from faulty or malicious software, and must not be able to destroy itself as a result of it.** A device that can destroy itself when running custom software — overcharging its battery, burning out its CPU, or exceeding safe RF output — is a fundamentally defective hardware design. The firmware should never be the last line of defence against hardware damage. If it is, that is a manufacturing flaw, not a user error.

We have seen this play out in practice. A Xiaomi device we worked on had a firmware issue — in the official manufacturer software — where the charging voltage was set slightly above the battery's rated maximum. The official Xiaomi charging app was actively managing and capping the charge cycle in software, masking the underlying issue. When the phone was powered off or running a custom ROM without that app, the underlying PMU protection should have been sufficient to prevent overcharging on its own — but it was not. Whether this was a deliberate design decision or an oversight, we cannot say. What we can say is that the charging voltage exceeded the battery's rated maximum, and the hardware did not catch it independently. The custom ROM did not introduce the problem — it removed the software layer that had been compensating for it, exposing what was already there.

That is the core point: the device was shipped with hardware that relied on a specific software layer to remain safe. That is, by definition, a hardware defect — not a reason to void a warranty.

The warranty void argument is therefore wrong on two levels: legally, because EU law requires proof of causation rather than just proof of modification; and technically, because properly designed hardware does not depend on firmware to enforce its own safety limits.

---

## The Xiaomi story: a case study in control

Xiaomi officially states that it locks bootloaders to "enhance security, protect user data, and ensure a stable user experience." In practice, the policy tells a very different story — and the commercial motivations become visible once you look closely.

Over the years, Xiaomi has progressively tightened the unlock process to the point where it feels less like a security measure and more like an endurance test designed to make users give up. SMS verification, geolocation checks, daily request caps that fill almost instantly, multi-day waiting periods, and narrow completion windows all stack on top of each other. Miss any step, and you start from scratch.

There is also a less-discussed commercial reason behind the tightening: for years, companies were purchasing cheap Chinese Xiaomi variants, flashing global firmware, and reselling them worldwide at a profit — bypassing Xiaomi's regional pricing entirely. The increasingly restrictive unlock process is almost certainly partly a response to this. The problem is that it punishes every legitimate user in the process.

The situation differs between regions. Chinese ROM devices face the harshest restrictions, with unlocking effectively blocked for many models. Global devices with a global account can still unlock on many models — the Redmi Note 15 5G being a current example — but the process is deliberately obstructive and the rules can change at any time without notice.

One long-time Xiaomi user on XDA put it plainly: *"I've had a Xiaomi phone for 8 years, long life due to custom ROMs — but without this possibility, Xiaomi loses all appeal."*

The direction of travel is clear. The window for unlocking Xiaomi devices is narrowing. If you own one and care about this, do it while you still can.

And while you are considering your next Xiaomi purchase — that shiny new Redmi Note 15? Look carefully. What you are largely buying is the same Redmi Note 12 from three years ago, slightly faster, with new branding. The firmware and kernel are often the same underneath. And because it ships with Android 15 and HyperOS 2.2 — bloated, locked, unauditable — it will frequently feel slower in daily use than a custom ROM running on the older device. You are paying for the box, not the freedom.

---

## Google's app store monopoly: the same fight

Bootloader locking is not the only front in this battle. The app ecosystem is under an equally serious threat — and it is coming from Google directly. The fire door is bolted shut, and you cannot get out.

For fifteen years, F-Droid has provided a safe space for Android users to find and install free and open source apps, with every app reviewed to ensure it contains no undocumented trackers or advertisements. AuroraStore allows users to download apps from Google Play without a Google account, avoiding mandatory data harvesting.

Google is now threatening to end this. Google has unilaterally decreed that Android developers everywhere will be required to register centrally — demanding payment of a registration fee, agreement to non-negotiable terms, uploading of government ID, and enumeration of all unique application identifiers for every app to be distributed. If put into effect, this developer registration decree will end F-Droid and other free and open source app distribution sources as we know them today.

The justification offered is security — but Google Play itself has repeatedly hosted malware, proving that corporate gatekeeping does not guarantee user protection. F-Droid's position is clear: this is not about security — it is about consolidating power and tightening control over a formerly open ecosystem.

Forcing software creators into a centralised registration scheme to distribute their work is an offense to the core principles of free speech and thought that are central to democratic societies. The right to run software you trust, on hardware you own, without asking permission from a platform gatekeeper, is a single coherent principle — and it is under attack on multiple fronts simultaneously, while the fire door is bolted shut and you cannot get out.

---

## The right to repair — and the right to keep repairing

A locked bootloader directly works against the EU's Right to Repair goals. When a manufacturer stops providing official software updates — often after just a few years — a locked bootloader means you cannot install a custom operating system to keep the device running. This artificially shortens its useful life and pushes consumers into buying a replacement sooner than necessary.

It also removes the ability for community repair initiatives — such as Repair Cafés, operating across the EU, helping people fix their devices for free — to perform software repairs independently. A Repair Café volunteer can replace a cracked screen or a worn battery. But if the software is broken and the bootloader is locked, there is nothing they can do. The device becomes unrepairable through no fault of its hardware.

### EDL mode — the last resort for repairs — is also being locked down

EDL (Emergency Download) mode is the low-level recovery tool used when a device is completely unresponsive. Increasingly, manufacturers are locking even this behind a server-side authentication check. Your device must contact the manufacturer's servers to verify whether you are "allowed" to repair your own property. If they say no, or if their servers are unavailable, the repair simply cannot proceed.

The real-world consequences are serious. A Xiaomi device bricked by an official Xiaomi software update could not be recovered even by Xiaomi's own authorised repair partner — because EDL authentication blocked the repair. The device had to be sent to Xiaomi directly, and nowhere else. They replaced the entire mainboard. Everything — personal data, photos, messages, years of content — was lost permanently and unnecessarily. The owner was refused the EDL key despite having every right to it. A software problem that could have been fixed by reinstalling the operating system was treated as cause for a full hardware replacement, simply because the repair tools were locked behind a manufacturer gate.

The same situation with another device after the two-year warranty period would have meant paying out of pocket for that same unnecessary hardware replacement — sent to Xiaomi only, independent repair explicitly refused, the EDL key withheld from the owner of the device.

Meanwhile, our [Android Live Recovery USB Toolkit](https://xdaforums.com/t/android-live-recovery-usb-bootable-toolkit-for-flashing-recovering-and-de-bricking-xiaomi-motorola-oneplus-and-samsung-devices-20-august-2025.4755466/) live USB image — a bootable USB tool for flashing, recovering, and de-bricking Xiaomi, Motorola, OnePlus, and Samsung devices — can repair the operating system entirely, without asking anyone's permission. The hardware was fine. The software was fixable. The only thing standing in the way was a manufacturer authentication gate.

---

## Against EU sustainability goals and planned obsolescence

The EU has set clear sustainability goals: products should last longer, generate less waste, and be repairable. Bootloader locking is a direct mechanism for planned obsolescence.

Consider what is actually possible when hardware is treated with respect:

- A **2007 Panasonic Toughbook** runs Linux with full disk encryption today without issues.
- A **Raspberry Pi Model B**, released in February 2012, is still in active use running Linux.
- A **Samsung Galaxy S (GT-I9000)** from 2010 and two **OnePlus X (Onyx)** devices from 2016 still serve as dedicated security cameras, running continuously around the clock on LineageOS.
- A **Samsung Galaxy Note 10.1 (2014)** is still receiving custom [Android 13 (LineageOS 20) builds](https://xdaforums.com/t/lineageos-ul-20-0-rom-unofficial-android-13-microg-magisk-twrp-samsung-galaxy-note-10-1-2014-sm-p600-n1awifi-05-juli-2025.4726458/) in 2026 — thirteen years after manufacture, years after Samsung abandoned it, with an update currently in progress.

None of this is possible without open software access and dedicated developers who spend countless hours of their own time for free, developing ROMs and tools for these devices — with more dedication than the original manufacturer ever showed.

A device discarded after four years because the bootloader is locked and official support has ended — when it could have run for a decade with community software — is an environmental failure. Locking devices to accelerate replacement is, by any reasonable definition, planned obsolescence. And planned obsolescence is exactly what EU sustainability policy is supposed to prevent.

---

## Property rights

When you buy a device outright, you own it. You can shove it anywhere you like. A manufacturer placing permanent restrictions on what you can do with your own property is a significant interference with that ownership. They have been paid. They no longer hold the device. Yet they continue to dictate how it can be used. That is a difficult position to justify legally — and one that would never be accepted for any other category of consumer electronics.

---

## Privacy: what are they hiding?

A locked bootloader makes it effectively impossible for independent researchers to inspect what software is running on your device. Manufacturers collect enormous amounts of data every day — usage patterns, location data, app behaviour, and more. They push their own advertisements, bloatware, and services that cannot be removed. With a locked bootloader, you have no practical way to audit, limit, or remove any of this.

Some people respond with *"I have nothing to hide, so I have nothing to fear."* But think about what that actually means. You close the bathroom door not because you are doing something illegal, but because some things are not anyone else's business. You do not hand your diary to your employer just because you have nothing to hide. You draw the curtains at night not because you are a criminal, but because your home is your space. Privacy is not about guilt — it is about dignity, autonomy, and the basic right to a part of your life that belongs only to you.

Your device contains your messages, your medical searches, your financial activity, your location history, your photos, your political views, and your private conversations. A locked bootloader means you cannot verify what is being collected, where it is being sent, or who can access it. You are expected to simply trust the manufacturer — a company with a direct financial interest in your data.

Governments have also shown a consistent interest in accessing device data, sometimes through legal channels, sometimes less so. Even in countries with strong end-to-end encryption laws, history has shown that where a backdoor can exist, pressure will eventually be applied to use it. A locked bootloader, controlled entirely by the manufacturer, is a single point of control that is far easier to compromise or compel than an open, community-audited system.

Privacy should not be a luxury requiring an expensive specialised device. It should be the default.

---

## Who is doing this?

Not all manufacturers behave the same way. The community resource **[bootloader-unlock-wall-of-shame](https://github.com/zenfyrdev/bootloader-unlock-wall-of-shame)** on GitHub tracks this in detail.

### Complete lockdown — unlock not possible

Amazon, Apple, Huawei, Samsung (One UI 8 and newer), TCL/BlackBerry, Vivo/iQOO

### Unlock technically possible, but made deliberately difficult

Typically requiring a manufacturer account:

Hisense, HMD/Nokia, Honor, HTC, LG, Motorola/Lenovo/NEC, OPPO/Realme, Oukitel, Xiaomi/Redmi/POCO, ZTE/nubia

> Any unlock process requiring contact with a manufacturer server should not be fully trusted — because that server can be switched off, restricted, or used to deny your request at any time.

### Manufacturers that still allow unlocking with relatively few barriers

Blackview, Cubot, Fairphone, Google/Pixel, Micromax, Microsoft (Surface Duo), Nothing, OnePlus, Shift, Sony, Teclast, Teracube, TP-Link/Neffos, Ulefone, Umidigi, Volla

These manufacturers prove that user freedom and EU law are not in conflict. If you are buying a new device and care about owning what you pay for, this list is a good place to start.

---

## A note for developers, security researchers, and legal specialists

> *To be fully transparent: I am not a legal specialist. I am a white hat hacker, computer hardware engineer, and developer who knows when something is technically wrong and legally suspicious. I have lived closely with people working in legal fields for many years, had more debates with lawyers than I can count, and picked up a great deal along the way — but that does not make me one. The arguments here are based on my own reading, research, and experience — but I want to sit down with legal warriors and work out the best approach together. If you have expertise in EU law, consumer rights, or competition law, I genuinely want to hear from you in this thread.*

### For developers and security researchers

The legal arguments here need technical substantiation. Documented firmware vulnerabilities on locked devices, evidence of undisclosed data collection, or analysis showing bootloader locking provides no meaningful security benefit that less restrictive measures could not achieve — all of this is valuable. Documented cases of EDL authentication blocking legitimate repairs are especially useful. I have already started a legal process against a few manufacturers myself, but had to set it aside due to health issues. If you are willing to pick up where that left off or contribute your own work, say so below.

### For legal specialists and EU law practitioners

The core legal arguments are:

- Misuse of Delegated Act 2022/30/EU as justification for restrictions the directive does not require
- Conflict with the EU Right to Repair framework
- Violation of EU sustainability and Ecodesign objectives amounting to facilitated planned obsolescence
- Interference with property rights
- Potential abuse of a dominant repair position under competition law
- Google's monopolistic control over app distribution through its pushed framework and app store, which actively undermines open alternatives like F-Droid and AuroraStore

Viable routes include a formal complaint to the European Commission, a submission to the European Parliament's PETI committee, or a European Citizens' Initiative. I am not a lawyer — I need you. But I expect people with the same terrier and warrior mentality — not the flexible-spined type. You are not going to win a war with those.

### For journalists and policy researchers

This issue sits at the intersection of consumer rights, environmental policy, competition law, and digital freedom. It is underreported relative to its significance. Background, data, and technical sourcing are available on request. And if you can rewrite my story into something better and more compelling, you are more than welcome — I would rather stay the nerd and company owner who directs from the background than the one standing in the spotlight.

---

## What we want

We are calling on the EU to take the following concrete steps:

- **Clarify** that Delegated Act 2022/30/EU does not require permanent bootloader locking, and that manufacturers misrepresenting this must stop
- **Explicitly protect** the right of users to unlock the bootloader of a device they own, through a simple process requiring no manufacturer permission or account
- **Prohibit** all forms of manufacturer-controlled locks preventing independent repair and OS installation — including bootloader locks, EDL authentication gates, server-side unlock validation, and any equivalent mechanism devised in the future — whether in hardware, firmware, or software
- **Recognise** bootloader locking and EDL authentication as barriers to repair under Right to Repair legislation
- **Define** software-based planned obsolescence as a violation of EU sustainability and consumer protection law
- **Investigate** whether forcing users to send locked devices to manufacturers for software repairs constitutes an unfair repair monopoly under competition law, and extend that investigation to Google's monopolistic control over Android app distribution
- **Require transparency** about data collected and transmitted from locked devices, and give users meaningful tools to limit it
- **Protect alternative app distribution** by ensuring Google's developer registration requirements cannot be used to shut down F-Droid, AuroraStore, and other open distribution channels — in line with the EU Digital Markets Act

---

## What needs to happen — and how you can help

Most people will read this, agree, and do nothing. That is human nature and it is fine. But the people who *do* want to act need to find each other and divide the work.

### Vote for this cause

The most direct democratic tool available to EU citizens is the **European Citizens' Initiative**. If one million people across at least seven member states sign, the European Commission is legally obliged to consider the issue. You do not need to be a developer or a lawyer — you just need to be an EU citizen who believes you should own the device you paid for. If we get this off the ground, a link will appear here.

### If you have five minutes

Share this article — on XDA, Reddit, Mastodon, or anywhere people who care about digital rights gather.

### If you want to write

Draft a short message to your MEP at [europarl.europa.eu](https://www.europarl.europa.eu/meps/en/home). A personal message carries far more weight than a form letter. Share it here so others can adapt it.

### If you have legal knowledge

Post your analysis in this thread. Even a brief assessment of the strongest legal routes helps enormously. I am not a lawyer — I need you more than anyone else here. But I expect people with the same terrier and warrior mentality — not flexible spines, and not sheeple. You are not going to win a war with those types.

### If you want to coordinate

Someone needs to own the European Citizens' Initiative process — it has strict formal requirements. If that is you, say so.

### If you are a developer

Technical evidence that bootloader locking provides no security benefit that less restrictive measures could not achieve is the backbone of a legal challenge. Share it here.

---

The goal is not for one person to carry this. It is to find the ten or twenty people across Europe who each contribute one thing they are good at. If you are one of them, say so below.

---

*Do you agree? Share this article. The more of us pushing in the same direction, the harder we are to ignore.*
