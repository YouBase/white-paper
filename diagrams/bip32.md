graph LR

m(m)

m---youbase
m---wallet

subgraph bip43
  youbase(m/42' - youbase)
  wallet(m/44' - wallet)
end

youbase---health

subgraph Profiles
  health(m/42'/0 - health)
end

health---allergy
health---immunization

subgraph Collections
  allergy(m/42'/0/0 - allergies)
  immunization(m/42'/0/1 - immunizations)
end

allergy---nuts
allergy---cats

subgraph Records
  nuts(m/42'/0/0/0 - nuts)
  cats(m/42'/0/0/1 - cats)
end
