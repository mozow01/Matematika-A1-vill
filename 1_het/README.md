# Koordinátamentes vektorok

<img src="https://github.com/mozow01/mat_a1/blob/main/1_het/vektor_1.png" width=400>

````coq
Class Vek := Vek_mk {
  Vektor : Type;
  Skalar := nat; (*itt nat helyett valójában a valós számok!!! vannak, de hát, annyi baj legyen*)

  add_v : Vektor -> Vektor -> Vektor;
  mul_v : Skalar -> Vektor -> Vektor;
  nul_v : Vektor;
  neg_v : Vektor -> Vektor;

  komm:           forall u v : Vektor, add_v u v = add_v v u;
  asszoc:         forall u v w : Vektor, add_v (add_v u v) w = add_v u (add_v
                  v w);
  null_vek:       forall u : Vektor, add_v nul_v u = u /\ add_v u nul_v = u;
  ellentett_vek:  forall u : Vektor, add_v (neg_v u) u = nul_v /\ add_v u 
                  (neg_v u) = nul_v;

  vek_1 : forall u : Vektor, mul_v 1 u = u;
  vek_2 : forall (λ : Skalar) (u v : Vektor), mul_v λ (add_v u v) = add_v (mul_v λ u) (mul_v λ v) ;
  vek_3 : forall (λ μ : Skalar) (u : Vektor), mul_v (λ + μ) u = add_v (mul_v λ u) (mul_v μ u) ;
  vek_4 : forall (λ μ : Skalar) (u : Vektor), mul_v λ (mul_v μ u) = mul_v (λ * μ) u ;
}.

Notation "u ⊕ v" := (add_v u v) (at level 90, left associativity) : type_scope.

Notation "λ ⊙ u" := (mul_v λ u) (at level 90, left associativity) : type_scope.

Context (V : Vek).

Theorem beszorzás : forall (λ μ : Skalar) (u v : Vektor), ((λ + μ) ⊙ (u ⊕ v)) = ((λ ⊙ u) ⊕ (λ ⊙ v) ⊕ (μ ⊙ u) ⊕ (μ ⊙ v)).
Proof.
intuition.
rewrite vek_3.
rewrite vek_2.
rewrite -> vek_2.
rewrite asszoc.
rewrite -> asszoc.
rewrite asszoc.
auto.
Qed.
````
## Egyértelműségi lemma

## A paralelogramma átlói felezik egymást

## Egyenes egyenlete

## Skaláris szorzat és tulajdonságai

## Háromszög magasságpontjának kifejezése

## Vektoriális szorzat és tulajdonságai

## A szinusztétel bizonyítása

## Paralelepipedon térfogata
