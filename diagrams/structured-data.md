graph TD
seed(Seed)

seed---m
m(m)

m---wallet
m---youbase

subgraph Purpose
  wallet(m/44' - wallet)
  youbase(m/42' - youbase)
end

youbase---health
youbase---identity

subgraph Profiles
  health(m/42'/0' - health)
  identity(m/42'/1' - identity)
end

health---allergy
health---immunization

subgraph Collections
  allergy(m/42'/0'/0 - allergies)
  immunization(m/42'/0'/1 - immunizations)
end

allergy---nuts
allergy---cats

subgraph Records
  nuts(m/42'/0'/0/0 - nuts)
  cats(m/42'/0'/0/1 - cats)
end
