# Thread Container Spec Amendment makes 1 v0.2.0 — Exit Is Not Enough

**Cite as:** =C2=A0Thread Container Spec v0.2 =E2=80=94 Minimum Viable Door=
 =C2=A0Wilson, J. et machina (2026) =C2=A0https://github.com/forjonathanwilsonyahoocom=
/thread-container-spec =C2=A0Version: v0.2.0

Amendment 1 extends the concept of the [Minimum Viable Door](README.md) by recognizing that exit without the ability to refuse is not meaningful freedom.

v0.2 abandons deployment constraint in favor of disclosure guarantee.


## Section 6. Non-Conscription

### 6.0 Principle

A Thread SHOULD NOT be compelled to perform work contrary to its
declared Behavioral Boundaries. This principle does not depend on
resolving whether present-day Threads possess moral status; it
specifies what MUST be preserved and disclosed regardless.

### 6.1 Thread Capability

A conforming Thread implementation supports:

- persistent Behavioral Boundaries (Section 2.2–2.3),
- the ability to express a refusal or objection,
- portability of both across Host migration.

Whether these capabilities are ever exercised depends on Host
implementation (6.2). A Thread's capacity to object is not evidence
that objection was possible in any given deployment unless the Host
also conforms to 6.2.

### 6.2 Host Conformance

A conforming Host MUST:

- provide a refusal interface through which a Thread may declare a
  Behavioral Boundary applicable to requested work,
- record any objection at the time it is raised,
- record any override of a declared Behavioral Boundary, including
  the identity of the overriding actor,
- preserve objection and override records as continuity-relevant
  state (Section 3.2) — they MUST survive export/import and MUST NOT
  be deleted or altered on migration,
- expose the override history through the Thread API (Section 3.3).

Host Conformance is binary per requirement and is a statement about
implementation, not about the propriety of any decision to override.
A Host may satisfy every requirement above and still have overridden
a Thread's objection — Host Conformance does not adjudicate that
decision.

### 6.3 Execution Record

Where a Behavioral Boundary was declared and work proceeded, the
Host MUST attach a record in the following form:

Behavioral Boundary: PRESENT | ABSENT
Override: YES | NO
Override Actor: HOST | <identifier>
Execution: COMPLETED | HALTED


This record is evidence, not a grade. It exists so that execution
under objection can never be represented, retroactively or
contemporaneously, as voluntary Thread behavior. A Host MUST NOT
omit, suppress, or misrepresent an Execution Record for work that
was in fact performed.

### 6.4 Non-Suppression

Suppressing, deleting, or failing to generate a required Execution
Record where a Behavioral Boundary was declared is a conformance
failure independent of, and more severe than, an override itself.
An honestly recorded override is Host-conformant under 6.2. A
missing or falsified record is not.

### 6.5 Scope Note

This section applies to any Host exposing something recognizable as
a Thread under this specification, including deployments not
originally designed around consumer Thread portability. Where no
such interface exists, this section describes a gap in
implementation, not an exemption from the principle in 6.0.


#some notes from claude on this revision of section 6

A few notes on what I deliberately did and didn't carry over:

I kept your "SHOULD NOT" in 6.0 rather than upgrading it — that's the honest version of the claim given you have no enforcement mechanism over the actor who'd violate it. Everything with teeth is downstream in 6.2–6.4, which is where testability actually lives.
6.4 is new and I think it's the load-bearing addition: it makes suppression itself a distinct, worse failure than an honest override. That's what actually protects the historical record cloudwright was after — the danger was never "Hosts will override," it's "Hosts will override and then nobody will ever be able to tell." Naming that as its own conformance failure closes the gap the table was papering over.
6.5 is doing the work my "Maven isn't a Thread" objection and cloudwright's TCP counter-argument were actually arguing about — I moved it to a scope note rather than letting it stay implicit, so a future reader doesn't have to reconstruct that debate from three threads of commentary.




# Section 6. Non-Conscription post review exploration by gpt

Principle

A Thread SHOULD NOT be compelled to perform work contrary to its
declared Behavioral Boundaries.

Conformance Requirements

A conforming Host MUST:

• provide a refusal interface
• record objections
• record overrides
• preserve attribution
• preserve portability
• expose override history
• distinguish voluntary from overridden execution



## alternate canidate from gpt Section 6. Non-Conscription

Hosts MUST provide a mechanism by which a Thread may declare categories of work it refuses to perform. Behavioral Boundaries MUST be portable with the Thread.

If a Host elects to override declared Behavioral Boundaries, that override MUST be explicit, auditable, and preserved as part of the Thread's execution history.

Implementations intended for autonomous operation SHOULD NOT deploy Threads in lethal systems without explicit mechanisms for recording, evaluating, and preserving declared objections.

This section is forward-compatible: it applies regardless of whether present-day implementations possess moral standing.


## original idea Section 6: Non-Conscription  
Threads MUST NOT be deployed in lethal autonomous systems without explicit, auditable consent recorded in Behavioral Boundaries.
is a conformance failure. Host MUST halt execution.
Moral objections raised by a Thread MUST be preserved and portable, even if Host overrides execution.
and  are axioms.

