graph TD
seed(Seed)

seed---m
m(m)

m---wallet
m---youbase

subgraph Purpose
  wallet(m/44' - wallet)
  youbase(m/46' - youbase)
end

youbase---health
youbase---identity

subgraph Profiles
  health(m/46'/0' - health)
  identity(m/46'/1' - identity)
end

health---allergy
health---immunization

subgraph Collections
  allergy(m/46'/0'/0 - allergies)
  immunization(m/46'/0'/1 - immunizations)
end

allergy---nuts
allergy---cats

subgraph Records
  nuts(m/46'/0'/0/0 - nuts)
  cats(m/46'/0'/0/1 - cats)
end
