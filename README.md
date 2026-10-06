# Steward for Business

**A WhatsApp CFO agent that pays, protects and plans a small business's money on Airwallex.**

Entry for the [Airwallex Agentic Banking Hackathon](https://airwallex.hackerearth.com/) · Tracks 2 (Intent-Bound Purchase Agent), 3 (Payment Ops Incident Commander) and 1 (Adaptive Treasury Controller).

> Status: idea phase. The build runs Oct 25 – Nov 13, 2026; this repository will hold the code.

## The problem

Small business owners run their money from their phones, between customers. Paying suppliers, chasing late transfers and deciding what to pay when cash is short means opening banking dashboards they rarely use. Mistakes are costly: a supplier paid twice, or payroll missed because cash was stuck.

## The solution

Steward for Business is an AI agent that runs a small business's day-to-day money on **Airwallex**, controlled from **WhatsApp**.

| You text | The agent |
|---|---|
| "Pay Ada's invoice, $450" | Checks the balance, prepares the transfer, asks for one tap to approve. |
| "Our transfer to Kemi Supplies is late" | Checks the transfer's status and **refuses to pay again** until the first payment is confirmed failed. *(Track 3)* |
| "Approve our Figma plan up to $15/month" | Issues a **virtual card locked to that merchant and limit**; anything outside the approved terms is blocked and sent back to the owner. *(Track 2)* |
| *(every morning)* | "Cash is short this week: here's what I'd pay now, convert, or delay." The owner approves the plan. *(Track 1)* |

## Safety by design

The agent acts only within **hard limits it cannot override**:

- per-payment and daily caps, and approved payees only;
- card controls (merchant, amount, frequency) enforced by Airwallex Issuing;
- idempotent payment references, so a retry never pays twice;
- every action logged and explained in plain language;
- anything over a limit needs the owner's tap in WhatsApp.

The language model understands requests and proposes actions. Code checks every action against the limits before anything reaches Airwallex.

## Built on experience

The same safety model already runs in three live WhatsApp AI agents that move real money, each with strict wallet policies, tap-to-confirm, double-pay protection and real users:

- [Steward](https://github.com/Yilkash/steward): tokenized stocks and payments on Robinhood Chain
- [Sharebloom](https://github.com/Yilkash/sharebloom): tokenized stocks on BNB Chain
- [Pollenstocks](https://github.com/Yilkash/pollenstocks): tokenized stocks on Arc by Circle

## Planned stack

- **Airwallex APIs:** wallets and balances, transfers and beneficiaries, FX conversions, Issuing (virtual cards and spend controls), webhooks
- **WhatsApp Cloud API** for the conversation and approval buttons
- **Claude** with tool calling for understanding and planning
- **Next.js / TypeScript**, with a durable job runner and an audit log

## License

MIT
