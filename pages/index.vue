<template>
  <hoods-base-element
    :loading="false"
    :neighbourhood="neighbourhood"
    :error="error"
    language="fi"
  />
</template>

<script>
import { HoodsBaseElement, LoadHoodData } from '@hoods/hood-card-base-component'

const getCoordinates = ({ lat, lon }) => {
  if (lat && lon) {
    return {
      lat,
      lon
    }
  }

  return undefined
}

export default {
  components: {
    HoodsBaseElement
  },

  computed: {},

  asyncData({ query }) {
    return LoadHoodData({
      apiKey: query['api-key'],
      neighbourhoodId: query['neighbourhood-id'],
      municipalityId: query['municipality-id'],
      coordinates: getCoordinates({ lat: query.lat, lon: query.lon })
    })
  }
}
</script>
