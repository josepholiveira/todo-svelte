<script lang="ts">
  import ClipboardIcon from "../assets/clipboard.png";
</script>

<div>
  <img src={ClipboardIcon} alt="">
  <p><strong>You have no tasks yet.</strong></p>
  <p>Create tasks and organize yourself.</p>
</div>

<style>
  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 24px;
    border-top: 1px solid #333333;
  }

  img {
    margin-bottom: 1rem;
    margin-top: 4rem;
  }

  p {
    text-align: center;
    font-size: 1rem;
    color: var(--gray-300);
    line-height: 1.4;
  }
</style>