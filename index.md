---
layout: page
title: Fortress64 - Securing Your Digital Privacy
menubar: menu
---
# We Are Done Asking Permission to Use Our Own Devices
### A legal and technical case against bootloader locking — and a call to act

---

## Part 1: The Case — Samsung One UI 8

Samsung removed all bootloader unlock capability from One UI 8 — globally, permanently, without exception. Devices shipped with One UI 8 cannot be unlocked. Older devices updated to One UI 8 face the same outcome. And with every monthly security patch incrementing the bootloader revision number, rolling back to an unlockable version becomes permanently impossible.

The consequences are concrete: independent repair is killed, electronic waste accelerates, manufacturer data collection cannot be audited or challenged, and an artificial monopoly is created over software running on hardware you already paid for and own.

---

## Part 2: The Harms

### The "Warranty Void" Argument — Already in Use

Under EU law, modifying your device's software is not sufficient on its own to void your statutory warranty. The seller must demonstrate that the specific defect being claimed was **caused** by the software modification — the burden of proof lies with the manufacturer, not with you.

Two distinct warranty types exist in the EU:

- **Statutory warranty**: Mandatory by law, minimum two years, cannot be waived under any circumstances.
- **Voluntary warranty**: A commercial extension the manufacturer can legitimately restrict.

Manufacturers routinely conflate these, telling consumers their "warranty is void" without specifying which one. Most people assume they have lost all protection. In practice, only the optional commercial extension may be affected — and even that requires proven causation. A cracked screen, a failed antenna, a dead charging port — none of these are plausibly caused by custom software.

A related issue is manufacturers selling devices with bootloader unlock capability and later removing it through software updates — without notice, without consent, and without refund. A 2024 UK small claims ruling addressed exactly this: a buyer successfully claimed against a manufacturer that removed a promised unlock capability post-purchase, receiving a full refund including court fees. UK rulings carry no formal precedent in EU courts, but the principle is straightforward — if unlock capability was part of what you paid for, removing it after the sale is a breach of what was promised. That argument is available to EU consumers under existing consumer protection law, and does not require any new regulation to pursue.

### The Warranty Void Argument Also Fails Technically

Every modern device contains a PMU — a Power Management Unit — a dedicated hardware component that manages and enforces safe power limits independently of the software stack. Battery charging thresholds, CPU thermal limits — these are governed at the hardware level. The OS communicates requests; the hardware enforces its own limits regardless of what the software asks for.

A device that can physically damage itself when running custom software is a device with a hardware design defect. Firmware should never be the last line of defence against hardware damage.

We saw this directly: a Xiaomi device we worked on had a charging voltage set above the battery's rated maximum in the official firmware. The official app was compensating in software — masking the underlying issue. When the device ran a custom ROM, the PMU's hardware protections should have been sufficient. They were not. The problem was not introduced by the custom ROM. The custom ROM removed the software layer that had been hiding a factory defect.

### Right to Repair

A locked bootloader is directly incompatible with the EU's Right to Repair framework. When a manufacturer ends software support — typically after two to four years — a locked bootloader means the device cannot run community-maintained software. Repair Cafés across the EU can replace a screen or a battery. If the software is broken and the bootloader is locked, there is nothing else they can do.

EDL mode — the low-level recovery path used when a device is completely unresponsive — is also being locked down. Manufacturers increasingly require server-side authentication before EDL access is permitted. If the server says no, or is unavailable, the repair cannot proceed — even by the manufacturer's own authorised partners.

A Xiaomi device bricked by an official Xiaomi update could not be recovered even by Xiaomi's authorised repair partner, because EDL authentication blocked the process. The device was sent to Xiaomi directly. The mainboard was replaced. Years of personal data were permanently destroyed. A software problem, fixable by reinstalling the OS, was treated as cause for a full hardware replacement — because the repair tools were locked behind a manufacturer authentication gate. This happened both within and after the warranty period. In neither case did the lock protect the user — it protected the manufacturer's control over the repair process.

### Against EU Sustainability Goals

The EU has set explicit sustainability objectives: products should last longer, generate less waste, be repairable. What is possible when hardware is treated with respect for longevity:

- A Samsung Galaxy Note 10.1 (2014) receiving custom Android 13 builds in 2026 — thirteen years after manufacture, years after Samsung abandoned it.
- A Samsung Galaxy S (GT-I9000) from 2010 still running as a security camera on LineageOS.
- A Raspberry Pi Model B from 2012 still in active use.

None of this is possible without open software access. A device discarded after four years because the bootloader is locked and official support has ended — when it could run for a decade with community software — is an avoidable environmental failure. This is, by any reasonable definition, planned obsolescence. EU sustainability policy is supposed to prevent exactly this.

### Privacy

A locked bootloader makes independent inspection of the running software effectively impossible. Manufacturers collect usage patterns, location data, app behaviour, and more. With a locked bootloader, users have no practical way to audit, limit, or challenge any of this.

Your device contains messages, medical searches, financial activity, location history, and private communications. A locked bootloader means you cannot verify what is being collected, where it goes, or who can access it. Where a single point of control exists — held entirely by a manufacturer — pressure to exploit it tends to follow.

---

## Part 3: The Excuses — What Manufacturers Will Claim

The article most likely to be used as future regulatory cover is [this SamMobile piece](https://www.sammobile.com/news/the-real-reason-behind-samsungs-one-ui-8-bootloader-unlock-ban-is-an-eu-law/). It is worth reading carefully — because some of it is true or will become true.

The dominant platforms controlling our devices are based entirely outside Europe. A locked Android device depends on Google's servers to function. Google is a US company, subject to US law and executive orders.

***In a worst-case scenario, the same administration that can flip a switch on trade tariffs could compel US technology companies to degrade, restrict, or brick devices in foreign markets — through entirely legal corporate compliance, not a cyberattack. A device running open, community-maintained software on unlocked hardware is immune to that threat. A locked device running proprietary software that phones home to, and honors servers in California is not.***

**Europe cannot claim digital sovereignty while every phone in its citizens' pockets is a locked, foreign-controlled endpoint.**

What manufacturers actually gain from locking has nothing to do with security:

- A locked device creates a captive audience for the manufacturer's app store, advertising platform, and services. Bloatware cannot be removed. Data collection cannot be audited.
- Google routes every user back through Google Play — capturing its 15–30% cut of every purchase. F-Droid, Accrescent, and Obtainium offer distribution outside Google's control. A locked ecosystem eliminates that alternative. Beyond the store itself, many apps require Google Play Services or the Google Services Framework to function at all — deeply embedded proprietary components that handle notifications, authentication, location, and more. Alternatives like MicroG can replicate some of this functionality, but only partially. On a locked device running stock firmware, there is no practical way to replace or audit these components — they run silently, with broad system permissions, on hardware you own.
- Locking reduces support costs: a bricked device that can't self-recover becomes a billable repair instead of a five-minute reflash — and a convenient reason to void the warranty if unlocked, although as outlined above, doing so is illegal in Europe.
- Locked devices accelerate the replacement cycle. A phone that can't run community software after manufacturer support ends becomes e-waste sooner. Another sale. The environmental cost is externalised; the profit is not.

### The Radio Equipment Directive — Not Currently Cited, But Worth Pre-empting

The Radio Equipment Directive, expanded by Delegated Act 2022/30/EU (effective August 2025), defines three cybersecurity outcomes: no network interference, data privacy, and anti-fraud protections for financial devices. It defines outcomes, not implementation methods — and says nothing about bootloader state. Its software verification clause narrowly targets radio frequency compliance only. No manufacturer has officially cited it as justification for permanent bootloader locking at the time of writing. Critically, the directive contains an explicit clause stating that software verification mechanisms must not be used to prevent the use of software from independent parties.

The argument that it justifies permanent locking fails on four grounds:

**1. Radio compliance is the modem's job — and the isolation extends further than most realise.** The cellular modem handles frequency compliance in isolation from the OS. Fairphone has [documented this explicitly](https://support.fairphone.com/hc/en-us/articles/10492476238865-How-to-unlock-and-re-lock-the-bootloader): the modem's isolation allows bootloader unlocking without implicating radio frequency compliance at all. Custom ROMs do not modify radio or modem behaviour. The same principle applies to WiFi firmware and eSIM profiles, which reside in a dedicated eUICC chip — a separate secure element the OS cannot directly access. The bootloader is simply not in the chain of trust for any of these components.

**2. A custom ROM can be more secure than stock.** The directive requires security — not manufacturer exclusivity. GrapheneOS is widely regarded by security researchers as more secure than stock Android: open to scrutiny, faster to patch, with no commercial incentive to delay disclosures.

**3. Laptops use the same framework — and are not locked.** Windows laptops fall under the same EU cybersecurity and radio equipment rules. No manufacturer locks their bootloader to block Linux. That inconsistency has no technical explanation.

**4. The directive protects networks, not business models.** Articles 3(3)(d), (e), and (f) cover network interference, data privacy, and fraud protection. They do not mention OS modifications, alternative software, or owner-initiated unlocking.

---

## Part 4: The Deeper Problem — Google's Monopoly by Proxy

This is not just about individual manufacturers. Google has a direct commercial interest in keeping devices locked — and the pattern of manufacturer behaviour reflects that pressure. The open alternatives that exist outside Google's ecosystem — F-Droid, Accrescent, Obtainium, MicroG — only remain viable as long as users can actually run them. A locked bootloader and a locked ecosystem are the hardware guarantee that most cannot.

Google is now building that control into three interlocking layers — each one tightening the next.

**Layer 1 — Play Integrity API (already active):** Since May 2025, Google has rolled out hardware-backed integrity verdicts by default on all Android 13 and above devices — no developer opt-in required. Unlocking the bootloader causes devices to fail these checks, locking users out of banking apps, payment platforms, and medical apps. The definition of a "genuine" Android device is explicitly one running a Google-certified build. Every custom ROM fails by design — though projects like crDroid have patched around this to some extent. It is an ongoing effort that requires work with every new Android release and is never fully guaranteed.

There is a deeper problem with banking apps requiring a locked bootloader. A well-built banking app should secure itself — through proper certificate pinning, encrypted communication, and server-side fraud detection — regardless of what is running underneath it. An app that refuses to function unless the bootloader is locked is not protecting the user; it is outsourcing its own security to Google's infrastructure and a manufacturer's hardware lock. The Play Integrity API only partially addresses one of seven categories in the OWASP Mobile Application Security Verification Standard — it covers platform trust, but says nothing about network security, data storage, authentication, or cryptography. A bank that blocks your access because your bootloader is unlocked, while running its own app with inadequate encryption or poor API security, has its priorities backwards. At most, an unlocked bootloader warrants a warning. Blocking access entirely is a convenience for the app developer, not a security measure for the user — and it hands Google a structural chokehold over which devices are permitted to participate in financial life.

**Layer 2 — Developer registration decree (rolling out 2026–2027):** Google has announced that all Android developers — not just Play Store publishers — will be required to register centrally, paying a fee, submitting government ID, and enumerating every application identifier for every app they distribute. This applies to sideloading too. F-Droid cannot require developers to register through Google, but equally cannot take over application identifiers for the apps it distributes — that would seize exclusive distribution rights. There is no structural exit. If enforced, this ends independent app distribution as it currently exists. Google Play has itself repeatedly hosted malware, which makes the security justification disingenuous — Google already has Play Protect, which scans and disables malicious apps regardless of their origin. This is about control, not safety. *(Source: [F-Droid — Google's Developer Registration Decree](https://f-droid.org/2025/09/29/google-developer-registration-decree.html))*

**Layer 3 — The bootloader as foundation:** These two layers only work if the device stays in Google's certified ecosystem. A locked bootloader is the hardware guarantee that it does. Unlocked devices fail integrity checks. Custom ROM users lose access to apps they depend on. The bootloader lock is not a standalone manufacturer decision — it is the hardware foundation the entire control stack is built on.

The parallel to Microsoft's browser monopoly case is direct. In the late 1990s, EU and US courts found that Microsoft had illegally abused its dominant position by bundling Internet Explorer with Windows — not because the browser was harmful, but because it used control over the OS to foreclose competition in an adjacent market. Google is doing the same thing at the platform level: using Android certification, the Play Store, the Play Integrity API, and developer registration requirements to eliminate competition in app distribution — with the locked bootloader as the enforcement mechanism at the hardware level. Manufacturers who want access to Google's services — Maps, Gmail, the Play Store itself — must meet Google's compatibility requirements. Those requirements create powerful structural incentives to keep devices locked. The pressure does not need to be explicit to be real.

This is precisely the behaviour the EU Digital Markets Act was designed to address. It should be applied — to the Play Integrity API, to the developer registration decree, and to the structural pressure Google places on manufacturers through its certification requirements.

---

## Part 5: Who We Are

I have been a Linux and Android developer since the early days. I respect my privacy and will keep my identity to myself. On XDA, some users have accepted manufacturer restrictions as inevitable — others repeat manufacturer talking points without examining them. Others, like me and my former team, have been actively cracking the "security" measures manufacturers impose, demonstrating in practice that these locks serve control rather than protection.

I have never been comfortable with software I cannot inspect or control. When the next SSH xz-style backdoor, the next Stagefright, the next QuadRooter appears — sitting unpatched on a locked device where neither the user nor independent researchers can do anything about it — that is not a theoretical concern. Privacy is not a personal preference you can opt out of on behalf of others. Your comfort with data collection does not give manufacturers the right to collect mine.

---

## Part 6: What We're Asking and How to Help

### Concrete asks for the EU

1. **Declare** that bootloader locking, EDL locking, and similar restrictions on computer systems — as well as ecosystem monopoly practices — are illegal and must be ended on short notice. The EU Right to Repair Act becomes active in July 2026. Manufacturers have had years to adapt their software. Instead, they are locking down everything they can before that deadline arrives.
2. **Protect** the right of device owners to unlock their bootloader through a straightforward, manufacturer-independent process. One practical model: include a scratch-card or equivalent with every device containing a verifiable unlock code, cross-referenceable on the manufacturer's website, that confirms the device is authentic and unmodified — without requiring any server connection, account, or manufacturer permission to proceed.
3. **Prohibit** manufacturer-controlled mechanisms preventing independent repair — bootloader locks, EDL authentication gates, and any equivalent future mechanism.
4. **Define** software-based planned obsolescence as a violation of EU sustainability and consumer protection law.
5. **Investigate** whether forcing users to send locked devices to manufacturers for software repairs constitutes an unfair repair monopoly under competition law.
6. **Protect** alternative app distribution — F-Droid, Accrescent, Obtainium — from being shut down through Google's developer registration requirements, in line with the Digital Markets Act. Further, require that Android devices can operate fully without Google Play Services or the Google Services Framework. Where apps depend on shared framework functionality, the relevant interfaces must be made available to open-source projects such as MicroG so that users are not structurally dependent on a single proprietary vendor to use hardware they own.

### Who the manufacturers are

The community resource [bootloader-unlock-wall-of-shame](https://github.com/melontini/bootloader-unlock-wall-of-shame) tracks this across manufacturers.

**Complete lockdown:** Amazon, Apple, Huawei, Samsung (One UI 8+), TCL/BlackBerry, Vivo/iQOO

**Technically possible, deliberately obstructed:** Hisense, HMD/Nokia, Honor, HTC, LG, Motorola/Lenovo, OPPO/Realme, Xiaomi/Redmi/POCO, ZTE/nubia

**Relatively accessible:** Fairphone, Google/Pixel, Nothing, OnePlus, Shift, Sony, and others

If you are purchasing a new device, that last list is a reasonable starting point.

### How you can help

**Five minutes:** Share this article on XDA, Reddit, Mastodon, or wherever people who care about digital rights gather.

**Legal expertise:** If you are an EU law practitioner, the core arguments are here — misrepresentation of the directive, conflict with Right to Repair, facilitated planned obsolescence, post-sale property rights, competition law, and the Digital Markets Act. Viable routes include a formal complaint to the European Commission, a submission to the PETI committee, or a European Citizens' Initiative. Post your analysis below.

**Technical evidence:** Documentation that permanent bootloader locking provides no security benefit that less restrictive measures could not achieve is the backbone of any legal challenge. We already have significant evidence presented here — but more is better. If you have it, share it.

The window is not unlimited. Manufacturers are organised and lobbying actively. Once these restrictions entrench further in regulation or customer acceptance, reversing them becomes significantly harder than preventing them now.

If you are one of the people this is written for — say so below.

---

*"The only thing necessary for the triumph of evil is for good men to do nothing." — Edmund Burke*
